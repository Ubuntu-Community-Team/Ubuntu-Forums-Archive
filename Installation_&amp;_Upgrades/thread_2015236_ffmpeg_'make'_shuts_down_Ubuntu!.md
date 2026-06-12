---
title: "ffmpeg 'make' shuts down Ubuntu!"
date: 2012-07-02
forum: Installation &amp; Upgrades
---

### Post by taskbask on 2012-07-02
I have an old IBM T40 thinkpad laptop. I have installed ubuntu 11.10 (32-bit) on it and I wanted to install the latest ffmpeg for use in OpenCV with python bindings. 

I did a ./configure, which succeeds. The commands I used were:
```

$ git clone --depth 1 git://git.videolan.org/ffmpeg
$ cd ffmpeg
$ ./configure --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb \
 --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 \
 --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab --enable-shared

```

When I try to make, ffmpeg begins compiling but at some point I get a black screen with a bunch of text. The text flashes by too fast to read, and then I see Ubuntu's logo in the center and the 5 loading dots beneath it. After this, the laptop shuts off. 

I have also tried to do a broken install (without yasm) of ffmpeg on the livecd and the same thing happens. 

I don't think it's a heat problem since I placed a fan underneath the laptop just for good measure.

Here is the syslog if it helps. I am unsure what else to examine 
```


Jul  2 13:06:33 water kernel: imklog 5.8.1, log source = /proc/kmsg started.
Jul  2 13:06:33 water rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="509" x-info="http://www.rsyslog.com"] start
Jul  2 13:06:33 water rsyslogd: rsyslogd's groupid changed to 103
Jul  2 13:06:33 water rsyslogd: rsyslogd's userid changed to 101
Jul  2 13:06:33 water rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul  2 13:06:33 water kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  2 13:06:33 water kernel: [    0.000000] Initializing cgroup subsys cpu
Jul  2 13:06:33 water kernel: [    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
Jul  2 13:06:33 water kernel: [    0.000000] KERNEL supported cpus:
Jul  2 13:06:33 water kernel: [    0.000000]   Intel GenuineIntel
Jul  2 13:06:33 water kernel: [    0.000000]   AMD AuthenticAMD
Jul  2 13:06:33 water kernel: [    0.000000]   NSC Geode by NSC
Jul  2 13:06:33 water kernel: [    0.000000]   Cyrix CyrixInstead
Jul  2 13:06:33 water kernel: [    0.000000]   Centaur CentaurHauls
Jul  2 13:06:33 water kernel: [    0.000000]   Transmeta GenuineTMx86
Jul  2 13:06:33 water kernel: [    0.000000]   Transmeta TransmetaCPU
Jul  2 13:06:33 water kernel: [    0.000000]   UMC UMC UMC UMC
Jul  2 13:06:33 water kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  2 13:06:33 water kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jul  2 13:06:33 water kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jul  2 13:06:33 water kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Jul  2 13:06:33 water kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Jul  2 13:06:33 water kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000005ff60000 (usable)
Jul  2 13:06:33 water kernel: [    0.000000]  BIOS-e820: 000000005ff60000 - 000000005ff77000 (ACPI data)
Jul  2 13:06:33 water kernel: [    0.000000]  BIOS-e820: 000000005ff77000 - 000000005ff79000 (ACPI NVS)
Jul  2 13:06:33 water kernel: [    0.000000]  BIOS-e820: 000000005ff80000 - 0000000060000000 (reserved)
Jul  2 13:06:33 water kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
Jul  2 13:06:33 water kernel: [    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
Jul  2 13:06:33 water kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Jul  2 13:06:33 water kernel: [    0.000000] DMI present.
Jul  2 13:06:33 water kernel: [    0.000000] DMI: IBM 237392U/237392U, BIOS 1RETDMWW (3.18 ) 09/15/2005
Jul  2 13:06:33 water kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jul  2 13:06:33 water kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jul  2 13:06:33 water kernel: [    0.000000] last_pfn = 0x5ff60 max_arch_pfn = 0x100000
Jul  2 13:06:33 water kernel: [    0.000000] MTRR default type: uncachable
Jul  2 13:06:33 water kernel: [    0.000000] MTRR fixed ranges enabled:
Jul  2 13:06:33 water kernel: [    0.000000]   00000-9FFFF write-back
Jul  2 13:06:33 water kernel: [    0.000000]   A0000-BFFFF uncachable
Jul  2 13:06:33 water kernel: [    0.000000]   C0000-CFFFF write-protect
Jul  2 13:06:33 water kernel: [    0.000000]   D0000-DBFFF uncachable
Jul  2 13:06:33 water kernel: [    0.000000]   DC000-DFFFF write-back
Jul  2 13:06:33 water kernel: [    0.000000]   E0000-FFFFF write-protect
Jul  2 13:06:33 water kernel: [    0.000000] MTRR variable ranges enabled:
Jul  2 13:06:33 water kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Jul  2 13:06:33 water kernel: [    0.000000]   1 base 040000000 mask FE0000000 write-back
Jul  2 13:06:33 water kernel: [    0.000000]   2 base 05FF80000 mask FFFF80000 uncachable
Jul  2 13:06:33 water kernel: [    0.000000]   3 disabled
Jul  2 13:06:33 water kernel: [    0.000000]   4 disabled
Jul  2 13:06:33 water kernel: [    0.000000]   5 disabled
Jul  2 13:06:33 water kernel: [    0.000000]   6 disabled
Jul  2 13:06:33 water kernel: [    0.000000]   7 disabled
Jul  2 13:06:33 water kernel: [    0.000000] PAT not supported by CPU.
Jul  2 13:06:33 water kernel: [    0.000000] original variable MTRRs
Jul  2 13:06:33 water kernel: [    0.000000] reg 0, base: 0GB, range: 1GB, type WB
Jul  2 13:06:33 water kernel: [    0.000000] reg 1, base: 1GB, range: 512MB, type WB
Jul  2 13:06:33 water kernel: [    0.000000] reg 2, base: 1572352KB, range: 512KB, type UC
Jul  2 13:06:33 water kernel: [    0.000000] total RAM covered: 1535M
Jul  2 13:06:33 water kernel: [    0.000000] Found optimal setting for mtrr clean up
Jul  2 13:06:33 water kernel: [    0.000000]  gran_size: 64K 	chunk_size: 1M 	num_reg: 3  	lose cover RAM: 0G
Jul  2 13:06:33 water kernel: [    0.000000] New variable MTRRs
Jul  2 13:06:33 water kernel: [    0.000000] reg 0, base: 0GB, range: 1GB, type WB
Jul  2 13:06:33 water kernel: [    0.000000] reg 1, base: 1GB, range: 512MB, type WB
Jul  2 13:06:33 water kernel: [    0.000000] reg 2, base: 1572352KB, range: 512KB, type UC
Jul  2 13:06:33 water kernel: [    0.000000] initial memory mapped : 0 - 01c00000
Jul  2 13:06:33 water kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Jul  2 13:06:33 water kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jul  2 13:06:33 water kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Jul  2 13:06:33 water kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Jul  2 13:06:33 water kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Jul  2 13:06:33 water kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
Jul  2 13:06:33 water kernel: [    0.000000] RAMDISK: 365fa000 - 372f5000
Jul  2 13:06:33 water kernel: [    0.000000] ACPI: RSDP 000f6d70 00024 (v02 IBM   )
Jul  2 13:06:33 water kernel: [    0.000000] ACPI: XSDT 5ff6a6cd 0004C (v01 IBM    TP-1R    00003180  LTP 00000000)
Jul  2 13:06:33 water kernel: [    0.000000] ACPI: FACP 5ff6a800 000F4 (v03 IBM    TP-1R    00003180 IBM  00000001)
Jul  2 13:06:33 water kernel: [    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 (20110413/tbfadt-529)
Jul  2 13:06:33 water kernel: [    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 0x000000000000102C/0x0 (20110413/tbfadt-560)
Jul  2 13:06:33 water kernel: [    0.000000] ACPI: DSDT 5ff6a9e7 0C4D5 (v01 IBM    TP-1R    00003180 MSFT 0100000E)
Jul  2 13:06:33 water kernel: [    0.000000] ACPI: FACS 5ff78000 00040
Jul  2 13:06:33 water kernel: [    0.000000] ACPI: SSDT 5ff6a9b4 00033 (v01 IBM    TP-1R    00003180 MSFT 0100000E)
Jul  2 13:06:33 water kernel: [    0.000000] ACPI: ECDT 5ff76ebc 00052 (v01 IBM    TP-1R    00003180 IBM  00000001)
Jul  2 13:06:33 water kernel: [    0.000000] ACPI: TCPA 5ff76f0e 00032 (v01 IBM    TP-1R    00003180 PTL  00000001)
Jul  2 13:06:33 water kernel: [    0.000000] ACPI: BOOT 5ff76fd8 00028 (v01 IBM    TP-1R    00003180  LTP 00000001)
Jul  2 13:06:33 water kernel: [    0.000000] 647MB HIGHMEM available.
Jul  2 13:06:33 water kernel: [    0.000000] 887MB LOWMEM available.
Jul  2 13:06:33 water kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jul  2 13:06:33 water kernel: [    0.000000]   low ram: 0 - 377fe000
Jul  2 13:06:33 water kernel: [    0.000000] Zone PFN ranges:
Jul  2 13:06:33 water kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jul  2 13:06:33 water kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jul  2 13:06:33 water kernel: [    0.000000]   HighMem  0x000377fe -> 0x0005ff60
Jul  2 13:06:33 water kernel: [    0.000000] Movable zone start PFN for each node
Jul  2 13:06:33 water kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul  2 13:06:33 water kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jul  2 13:06:33 water kernel: [    0.000000]     0: 0x00000100 -> 0x0005ff60
Jul  2 13:06:33 water kernel: [    0.000000] On node 0 totalpages: 392943
Jul  2 13:06:33 water kernel: [    0.000000] free_area_init_node: node 0, pgdat c17b11c0, node_mem_map f59fa200
Jul  2 13:06:33 water kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul  2 13:06:33 water kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul  2 13:06:33 water kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jul  2 13:06:33 water kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jul  2 13:06:33 water kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Jul  2 13:06:33 water kernel: [    0.000000]   HighMem zone: 1295 pages used for memmap
Jul  2 13:06:33 water kernel: [    0.000000]   HighMem zone: 164435 pages, LIFO batch:31
Jul  2 13:06:33 water kernel: [    0.000000] Using APIC driver default
Jul  2 13:06:33 water kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul  2 13:06:33 water kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jul  2 13:06:33 water kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Jul  2 13:06:33 water kernel: [    0.000000] APIC: disable apic facility
Jul  2 13:06:33 water kernel: [    0.000000] APIC: switched to apic NOOP
Jul  2 13:06:33 water kernel: [    0.000000] nr_irqs_gsi: 16
Jul  2 13:06:33 water kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul  2 13:06:33 water kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jul  2 13:06:33 water kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jul  2 13:06:33 water kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jul  2 13:06:33 water kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Jul  2 13:06:33 water kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 60000000:9f800000)
Jul  2 13:06:33 water kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul  2 13:06:33 water kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Jul  2 13:06:33 water kernel: [    0.000000] PERCPU: Embedded 12 pages/cpu @f5400000 s26240 r0 d22912 u4194304
Jul  2 13:06:33 water kernel: [    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
Jul  2 13:06:33 water kernel: [    0.000000] pcpu-alloc: [0] 0 
Jul  2 13:06:33 water kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 389872
Jul  2 13:06:33 water kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=6df79d67-e791-4ac7-a601-04b274f7b6fd ro quiet splash vt.handoff=7
Jul  2 13:06:33 water kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul  2 13:06:33 water kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul  2 13:06:33 water kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul  2 13:06:33 water kernel: [    0.000000] Initializing CPU#0
Jul  2 13:06:33 water kernel: [    0.000000] allocated 6288640 bytes of page_cgroup
Jul  2 13:06:33 water kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul  2 13:06:33 water kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0005ff60)
Jul  2 13:06:33 water kernel: [    0.000000] Memory: 1529628k/1572224k available (5329k kernel code, 42144k reserved, 2589k data, 696k init, 662920k highmem)
Jul  2 13:06:33 water kernel: [    0.000000] virtual kernel memory layout:
Jul  2 13:06:33 water kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Jul  2 13:06:33 water kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul  2 13:06:33 water kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jul  2 13:06:33 water kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jul  2 13:06:33 water kernel: [    0.000000]       .init : 0xc17bc000 - 0xc186a000   ( 696 kB)
Jul  2 13:06:33 water kernel: [    0.000000]       .data : 0xc1534784 - 0xc17bbd80   (2589 kB)
Jul  2 13:06:33 water kernel: [    0.000000]       .text : 0xc1000000 - 0xc1534784   (5329 kB)
Jul  2 13:06:33 water kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul  2 13:06:33 water kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Jul  2 13:06:33 water kernel: [    0.000000] Hierarchical RCU implementation.
Jul  2 13:06:33 water kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jul  2 13:06:33 water kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256 16
Jul  2 13:06:33 water kernel: [    0.000000] CPU 0 irqstacks, hard=f4806000 soft=f4808000
Jul  2 13:06:33 water kernel: [    0.000000] Extended CMOS year: 2000
Jul  2 13:06:33 water kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jul  2 13:06:33 water kernel: [    0.000000] Console: colour dummy device 80x25
Jul  2 13:06:33 water kernel: [    0.000000] console [tty0] enabled
Jul  2 13:06:33 water kernel: [    0.000000] Fast TSC calibration using PIT
Jul  2 13:06:33 water kernel: [    0.000000] Detected 1594.933 MHz processor.
Jul  2 13:06:33 water kernel: [    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3189.86 BogoMIPS (lpj=6379732)
Jul  2 13:06:33 water kernel: [    0.004013] pid_max: default: 32768 minimum: 301
Jul  2 13:06:33 water kernel: [    0.004050] Security Framework initialized
Jul  2 13:06:33 water kernel: [    0.004093] AppArmor: AppArmor initialized
Jul  2 13:06:33 water kernel: [    0.004096] Yama: becoming mindful.
Jul  2 13:06:33 water kernel: [    0.004196] Mount-cache hash table entries: 512
Jul  2 13:06:33 water kernel: [    0.004425] Initializing cgroup subsys cpuacct
Jul  2 13:06:33 water kernel: [    0.004435] Initializing cgroup subsys memory
Jul  2 13:06:33 water kernel: [    0.004450] Initializing cgroup subsys devices
Jul  2 13:06:33 water kernel: [    0.004454] Initializing cgroup subsys freezer
Jul  2 13:06:33 water kernel: [    0.004458] Initializing cgroup subsys net_cls
Jul  2 13:06:33 water kernel: [    0.004461] Initializing cgroup subsys blkio
Jul  2 13:06:33 water kernel: [    0.004473] Initializing cgroup subsys perf_event
Jul  2 13:06:33 water kernel: [    0.004527] mce: CPU supports 5 MCE banks
Jul  2 13:06:33 water kernel: [    0.004835] SMP alternatives: switching to UP code
Jul  2 13:06:33 water kernel: [    0.014436] Freeing SMP alternatives: 24k freed
Jul  2 13:06:33 water kernel: [    0.014450] ACPI: Core revision 20110413
Jul  2 13:06:33 water kernel: [    0.021752] ACPI: setting ELCR to 0200 (from 0800)
Jul  2 13:06:33 water kernel: [    0.024022] ftrace: allocating 24885 entries in 49 pages
Jul  2 13:06:33 water kernel: [    0.028144] weird, boot CPU (#0) not listed by the BIOS.
Jul  2 13:06:33 water kernel: [    0.028150] SMP motherboard not detected.
Jul  2 13:06:33 water kernel: [    0.028152] Local APIC not detected. Using dummy APIC emulation.
Jul  2 13:06:33 water kernel: [    0.028155] SMP disabled
Jul  2 13:06:33 water kernel: [    0.028158] Performance Events: 
Jul  2 13:06:33 water kernel: [    0.028162] no APIC, boot with the "lapic" boot parameter to force-enable it.
Jul  2 13:06:33 water kernel: [    0.028164] no hardware sampling interrupt available.
Jul  2 13:06:33 water kernel: [    0.028169] p6 PMU driver.
Jul  2 13:06:33 water kernel: [    0.028175] ... version:                0
Jul  2 13:06:33 water kernel: [    0.028178] ... bit width:              32
Jul  2 13:06:33 water kernel: [    0.028180] ... generic registers:      2
Jul  2 13:06:33 water kernel: [    0.028182] ... value mask:             00000000ffffffff
Jul  2 13:06:33 water kernel: [    0.028185] ... max period:             000000007fffffff
Jul  2 13:06:33 water kernel: [    0.028187] ... fixed-purpose events:   0
Jul  2 13:06:33 water kernel: [    0.028190] ... event mask:             0000000000000003
Jul  2 13:06:33 water kernel: [    0.028855] Brought up 1 CPUs
Jul  2 13:06:33 water kernel: [    0.028860] Total of 1 processors activated (3189.86 BogoMIPS).
Jul  2 13:06:33 water kernel: [    0.029070] devtmpfs: initialized
Jul  2 13:06:33 water kernel: [    0.029332] PM: Registering ACPI NVS region at 5ff77000 (8192 bytes)
Jul  2 13:06:33 water kernel: [    0.035934] print_constraints: dummy: 
Jul  2 13:06:33 water kernel: [    0.035962] Time: 17:06:12  Date: 07/02/12
Jul  2 13:06:33 water kernel: [    0.036061] NET: Registered protocol family 16
Jul  2 13:06:33 water kernel: [    0.036241] EISA bus registered
Jul  2 13:06:33 water kernel: [    0.036259] ACPI: bus type pci registered
Jul  2 13:06:33 water kernel: [    0.036663] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=8
Jul  2 13:06:33 water kernel: [    0.036666] PCI: Using configuration type 1 for base access
Jul  2 13:06:33 water kernel: [    0.038154] bio: create slab <bio-0> at 0
Jul  2 13:06:33 water kernel: [    0.040369] ACPI: EC: EC description table is found, configuring boot EC
Jul  2 13:06:33 water kernel: [    0.052561] ACPI: Interpreter enabled
Jul  2 13:06:33 water kernel: [    0.052568] ACPI: (supports S0 S3 S4 S5)
Jul  2 13:06:33 water kernel: [    0.052596] ACPI: Using PIC for interrupt routing
Jul  2 13:06:33 water kernel: [    0.056563] ACPI: Power Resource [PUBS] (on)
Jul  2 13:06:33 water kernel: [    0.060566] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Jul  2 13:06:33 water kernel: [    0.061104] ACPI: ACPI Dock Station Driver: 3 docks/bays found
Jul  2 13:06:33 water kernel: [    0.061104] HEST: Table not found.
Jul  2 13:06:33 water kernel: [    0.061104] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Jul  2 13:06:33 water kernel: [    0.061104] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul  2 13:06:33 water kernel: [    0.061104] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Jul  2 13:06:33 water kernel: [    0.061104] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Jul  2 13:06:33 water kernel: [    0.061104] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Jul  2 13:06:33 water kernel: [    0.061104] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
Jul  2 13:06:33 water kernel: [    0.061104] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
Jul  2 13:06:33 water kernel: [    0.061104] pci_root PNP0A03:00: host bridge window [mem 0x60000000-0xfebfffff] (ignored)
Jul  2 13:06:33 water kernel: [    0.061104] pci 0000:00:00.0: [8086:3340] type 0 class 0x000600
Jul  2 13:06:33 water kernel: [    0.061104] pci 0000:00:00.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
Jul  2 13:06:33 water kernel: [    0.061104] pci 0000:00:01.0: [8086:3341] type 1 class 0x000604
Jul  2 13:06:33 water kernel: [    0.061104] pci 0000:00:1d.0: [8086:24c2] type 0 class 0x000c03
Jul  2 13:06:33 water kernel: [    0.061104] pci 0000:00:1d.0: reg 20: [io  0x1800-0x181f]
Jul  2 13:06:33 water kernel: [    0.061115] pci 0000:00:1d.1: [8086:24c4] type 0 class 0x000c03
Jul  2 13:06:33 water kernel: [    0.061162] pci 0000:00:1d.1: reg 20: [io  0x1820-0x183f]
Jul  2 13:06:33 water kernel: [    0.061199] pci 0000:00:1d.2: [8086:24c7] type 0 class 0x000c03
Jul  2 13:06:33 water kernel: [    0.061245] pci 0000:00:1d.2: reg 20: [io  0x1840-0x185f]
Jul  2 13:06:33 water kernel: [    0.061292] pci 0000:00:1d.7: [8086:24cd] type 0 class 0x000c03
Jul  2 13:06:33 water kernel: [    0.061315] pci 0000:00:1d.7: reg 10: [mem 0xc0000000-0xc00003ff]
Jul  2 13:06:33 water kernel: [    0.061397] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jul  2 13:06:33 water kernel: [    0.061404] pci 0000:00:1d.7: PME# disabled
Jul  2 13:06:33 water kernel: [    0.061423] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
Jul  2 13:06:33 water kernel: [    0.061468] pci 0000:00:1f.0: [8086:24cc] type 0 class 0x000601
Jul  2 13:06:33 water kernel: [    0.061538] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH4 ACPI/GPIO/TCO
Jul  2 13:06:33 water kernel: [    0.061544] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH4 GPIO
Jul  2 13:06:33 water kernel: [    0.061561] pci 0000:00:1f.1: [8086:24ca] type 0 class 0x000101
Jul  2 13:06:33 water kernel: [    0.061576] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
Jul  2 13:06:33 water kernel: [    0.061588] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
Jul  2 13:06:33 water kernel: [    0.061599] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
Jul  2 13:06:33 water kernel: [    0.061610] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
Jul  2 13:06:33 water kernel: [    0.061621] pci 0000:00:1f.1: reg 20: [io  0x1860-0x186f]
Jul  2 13:06:33 water kernel: [    0.061633] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
Jul  2 13:06:33 water kernel: [    0.061663] pci 0000:00:1f.3: [8086:24c3] type 0 class 0x000c05
Jul  2 13:06:33 water kernel: [    0.061709] pci 0000:00:1f.3: reg 20: [io  0x1880-0x189f]
Jul  2 13:06:33 water kernel: [    0.061747] pci 0000:00:1f.5: [8086:24c5] type 0 class 0x000401
Jul  2 13:06:33 water kernel: [    0.061764] pci 0000:00:1f.5: reg 10: [io  0x1c00-0x1cff]
Jul  2 13:06:33 water kernel: [    0.061775] pci 0000:00:1f.5: reg 14: [io  0x18c0-0x18ff]
Jul  2 13:06:33 water kernel: [    0.061785] pci 0000:00:1f.5: reg 18: [mem 0xc0000c00-0xc0000dff]
Jul  2 13:06:33 water kernel: [    0.061796] pci 0000:00:1f.5: reg 1c: [mem 0xc0000800-0xc00008ff]
Jul  2 13:06:33 water kernel: [    0.061836] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Jul  2 13:06:33 water kernel: [    0.061841] pci 0000:00:1f.5: PME# disabled
Jul  2 13:06:33 water kernel: [    0.061858] pci 0000:00:1f.6: [8086:24c6] type 0 class 0x000703
Jul  2 13:06:33 water kernel: [    0.061875] pci 0000:00:1f.6: reg 10: [io  0x2400-0x24ff]
Jul  2 13:06:33 water kernel: [    0.061886] pci 0000:00:1f.6: reg 14: [io  0x2000-0x207f]
Jul  2 13:06:33 water kernel: [    0.061939] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
Jul  2 13:06:33 water kernel: [    0.061945] pci 0000:00:1f.6: PME# disabled
Jul  2 13:06:33 water kernel: [    0.061974] pci 0000:01:00.0: [1002:4c66] type 0 class 0x000300
Jul  2 13:06:33 water kernel: [    0.061990] pci 0000:01:00.0: reg 10: [mem 0xe0000000-0xe7ffffff pref]
Jul  2 13:06:33 water kernel: [    0.061999] pci 0000:01:00.0: reg 14: [io  0x3000-0x30ff]
Jul  2 13:06:33 water kernel: [    0.062008] pci 0000:01:00.0: reg 18: [mem 0xc0100000-0xc010ffff]
Jul  2 13:06:33 water kernel: [    0.062034] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Jul  2 13:06:33 water kernel: [    0.062055] pci 0000:01:00.0: supports D1 D2
Jul  2 13:06:33 water kernel: [    0.062091] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jul  2 13:06:33 water kernel: [    0.062096] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
Jul  2 13:06:33 water kernel: [    0.062101] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
Jul  2 13:06:33 water kernel: [    0.062106] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe7ffffff pref]
Jul  2 13:06:33 water kernel: [    0.062132] pci 0000:02:00.0: [104c:ac55] type 2 class 0x000607
Jul  2 13:06:33 water kernel: [    0.062150] pci 0000:02:00.0: reg 10: [mem 0xb0000000-0xb0000fff]
Jul  2 13:06:33 water kernel: [    0.062171] pci 0000:02:00.0: supports D1 D2
Jul  2 13:06:33 water kernel: [    0.062174] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  2 13:06:33 water kernel: [    0.062180] pci 0000:02:00.0: PME# disabled
Jul  2 13:06:33 water kernel: [    0.062199] pci 0000:02:00.1: [104c:ac55] type 2 class 0x000607
Jul  2 13:06:33 water kernel: [    0.062217] pci 0000:02:00.1: reg 10: [mem 0xb1000000-0xb1000fff]
Jul  2 13:06:33 water kernel: [    0.062238] pci 0000:02:00.1: supports D1 D2
Jul  2 13:06:33 water kernel: [    0.062241] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot D3cold
Jul  2 13:06:33 water kernel: [    0.062246] pci 0000:02:00.1: PME# disabled
Jul  2 13:06:33 water kernel: [    0.062274] pci 0000:02:01.0: [8086:101e] type 0 class 0x000200
Jul  2 13:06:33 water kernel: [    0.062295] pci 0000:02:01.0: reg 10: [mem 0xc0220000-0xc023ffff]
Jul  2 13:06:33 water kernel: [    0.062306] pci 0000:02:01.0: reg 14: [mem 0xc0200000-0xc020ffff]
Jul  2 13:06:33 water kernel: [    0.062317] pci 0000:02:01.0: reg 18: [io  0x8000-0x803f]
Jul  2 13:06:33 water kernel: [    0.062350] pci 0000:02:01.0: reg 30: [mem 0x00000000-0x0000ffff pref]
Jul  2 13:06:33 water kernel: [    0.064013] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
Jul  2 13:06:33 water kernel: [    0.064018] pci 0000:02:01.0: PME# disabled
Jul  2 13:06:33 water kernel: [    0.064039] pci 0000:02:02.0: [168c:0012] type 0 class 0x000200
Jul  2 13:06:33 water kernel: [    0.064058] pci 0000:02:02.0: reg 10: [mem 0xc0210000-0xc021ffff]
Jul  2 13:06:33 water kernel: [    0.064161] pci 0000:00:1e.0: PCI bridge to [bus 02-08] (subtractive decode)
Jul  2 13:06:33 water kernel: [    0.064167] pci 0000:00:1e.0:   bridge window [io  0x4000-0x8fff]
Jul  2 13:06:33 water kernel: [    0.064173] pci 0000:00:1e.0:   bridge window [mem 0xc0200000-0xcfffffff]
Jul  2 13:06:33 water kernel: [    0.064179] pci 0000:00:1e.0:   bridge window [mem 0xe8000000-0xefffffff pref]
Jul  2 13:06:33 water kernel: [    0.064183] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Jul  2 13:06:33 water kernel: [    0.064187] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
Jul  2 13:06:33 water kernel: [    0.064268] pci_bus 0000:00: on NUMA node 0
Jul  2 13:06:33 water kernel: [    0.064272] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul  2 13:06:33 water kernel: [    0.064327] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Jul  2 13:06:33 water kernel: [    0.064356] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Jul  2 13:06:33 water kernel: [    0.064469]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
Jul  2 13:06:33 water kernel: [    0.067736] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:06:33 water kernel: [    0.067844] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:06:33 water kernel: [    0.067948] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:06:33 water kernel: [    0.068064] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:06:33 water kernel: [    0.068148] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Jul  2 13:06:33 water kernel: [    0.068232] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Jul  2 13:06:33 water kernel: [    0.068316] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Jul  2 13:06:33 water kernel: [    0.068421] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:06:33 water kernel: [    0.068570] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jul  2 13:06:33 water kernel: [    0.068576] vgaarb: loaded
Jul  2 13:06:33 water kernel: [    0.068578] vgaarb: bridge control possible 0000:01:00.0
Jul  2 13:06:33 water kernel: [    0.068919] SCSI subsystem initialized
Jul  2 13:06:33 water kernel: [    0.069008] libata version 3.00 loaded.
Jul  2 13:06:33 water kernel: [    0.069081] usbcore: registered new interface driver usbfs
Jul  2 13:06:33 water kernel: [    0.069099] usbcore: registered new interface driver hub
Jul  2 13:06:33 water kernel: [    0.069135] usbcore: registered new device driver usb
Jul  2 13:06:33 water kernel: [    0.069257] PCI: Using ACPI for IRQ routing
Jul  2 13:06:33 water kernel: [    0.069396] PCI: pci_cache_line_size set to 64 bytes
Jul  2 13:06:33 water kernel: [    0.069466] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
Jul  2 13:06:33 water kernel: [    0.069470] reserve RAM buffer: 000000005ff60000 - 000000005fffffff 
Jul  2 13:06:33 water kernel: [    0.069629] NetLabel: Initializing
Jul  2 13:06:33 water kernel: [    0.069632] NetLabel:  domain hash size = 128
Jul  2 13:06:33 water kernel: [    0.069634] NetLabel:  protocols = UNLABELED CIPSOv4
Jul  2 13:06:33 water kernel: [    0.069652] NetLabel:  unlabeled traffic allowed by default
Jul  2 13:06:33 water kernel: [    0.069720] Switching to clocksource pit
Jul  2 13:06:33 water kernel: [    0.079702] AppArmor: AppArmor Filesystem Enabled
Jul  2 13:06:33 water kernel: [    0.079771] pnp: PnP ACPI init
Jul  2 13:06:33 water kernel: [    0.079803] ACPI: bus type pnp registered
Jul  2 13:06:33 water kernel: [    0.080494] pnp 00:00: [mem 0x00000000-0x0009ffff]
Jul  2 13:06:33 water kernel: [    0.080498] pnp 00:00: [mem 0x000c0000-0x000c3fff]
Jul  2 13:06:33 water kernel: [    0.080502] pnp 00:00: [mem 0x000c4000-0x000c7fff]
Jul  2 13:06:33 water kernel: [    0.080505] pnp 00:00: [mem 0x000c8000-0x000cbfff]
Jul  2 13:06:33 water kernel: [    0.080509] pnp 00:00: [mem 0x000cc000-0x000cffff]
Jul  2 13:06:33 water kernel: [    0.080512] pnp 00:00: [mem 0x000d0000-0x000d3fff]
Jul  2 13:06:33 water kernel: [    0.080515] pnp 00:00: [mem 0x000d4000-0x000d3fff disabled]
Jul  2 13:06:33 water kernel: [    0.080519] pnp 00:00: [mem 0x000d8000-0x000d7fff disabled]
Jul  2 13:06:33 water kernel: [    0.080523] pnp 00:00: [mem 0x000dc000-0x000dffff]
Jul  2 13:06:33 water kernel: [    0.080526] pnp 00:00: [mem 0x000e0000-0x000e3fff]
Jul  2 13:06:33 water kernel: [    0.080529] pnp 00:00: [mem 0x000e4000-0x000e7fff]
Jul  2 13:06:33 water kernel: [    0.080532] pnp 00:00: [mem 0x000e8000-0x000ebfff]
Jul  2 13:06:33 water kernel: [    0.080536] pnp 00:00: [mem 0x000ec000-0x000effff]
Jul  2 13:06:33 water kernel: [    0.080539] pnp 00:00: [mem 0x000f0000-0x000fffff]
Jul  2 13:06:33 water kernel: [    0.080553] pnp 00:00: [mem 0x00100000-0x5fffffff]
Jul  2 13:06:33 water kernel: [    0.080557] pnp 00:00: [mem 0xfec00000-0xffffffff]
Jul  2 13:06:33 water kernel: [    0.080681] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
Jul  2 13:06:33 water kernel: [    0.080687] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
Jul  2 13:06:33 water kernel: [    0.080691] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
Jul  2 13:06:33 water kernel: [    0.080695] system 00:00: [mem 0x000c8000-0x000cbfff] could not be reserved
Jul  2 13:06:33 water kernel: [    0.080700] system 00:00: [mem 0x000cc000-0x000cffff] could not be reserved
Jul  2 13:06:33 water kernel: [    0.080704] system 00:00: [mem 0x000d0000-0x000d3fff] could not be reserved
Jul  2 13:06:33 water kernel: [    0.080708] system 00:00: [mem 0x000dc000-0x000dffff] could not be reserved
Jul  2 13:06:33 water kernel: [    0.080713] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
Jul  2 13:06:33 water kernel: [    0.080717] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
Jul  2 13:06:33 water kernel: [    0.080721] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
Jul  2 13:06:33 water kernel: [    0.080726] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
Jul  2 13:06:33 water kernel: [    0.080730] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
Jul  2 13:06:33 water kernel: [    0.080734] system 00:00: [mem 0x00100000-0x5fffffff] could not be reserved
Jul  2 13:06:33 water kernel: [    0.080739] system 00:00: [mem 0xfec00000-0xffffffff] could not be reserved
Jul  2 13:06:33 water kernel: [    0.080745] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Jul  2 13:06:33 water kernel: [    0.080785] pnp 00:01: [bus 00-ff]
Jul  2 13:06:33 water kernel: [    0.080789] pnp 00:01: [io  0x0cf8-0x0cff]
Jul  2 13:06:33 water kernel: [    0.080792] pnp 00:01: [io  0x0000-0x0cf7 window]
Jul  2 13:06:33 water kernel: [    0.080796] pnp 00:01: [io  0x0d00-0xffff window]
Jul  2 13:06:33 water kernel: [    0.080799] pnp 00:01: [mem 0x000a0000-0x000bffff window]
Jul  2 13:06:33 water kernel: [    0.080803] pnp 00:01: [mem 0x000c0000-0x000c3fff window]
Jul  2 13:06:33 water kernel: [    0.080807] pnp 00:01: [mem 0x000c4000-0x000c7fff window]
Jul  2 13:06:33 water kernel: [    0.080810] pnp 00:01: [mem 0x000c8000-0x000cbfff window]
Jul  2 13:06:33 water kernel: [    0.080814] pnp 00:01: [mem 0x000cc000-0x000cffff window]
Jul  2 13:06:33 water kernel: [    0.080817] pnp 00:01: [mem 0x000d0000-0x000d3fff window]
Jul  2 13:06:33 water kernel: [    0.080821] pnp 00:01: [mem 0x000d4000-0x000d7fff window]
Jul  2 13:06:33 water kernel: [    0.080824] pnp 00:01: [mem 0x000d8000-0x000dbfff window]
Jul  2 13:06:33 water kernel: [    0.080828] pnp 00:01: [mem 0x000dc000-0x000dffff window]
Jul  2 13:06:33 water kernel: [    0.080832] pnp 00:01: [mem 0x000e0000-0x000e3fff window]
Jul  2 13:06:33 water kernel: [    0.080835] pnp 00:01: [mem 0x000e4000-0x000e7fff window]
Jul  2 13:06:33 water kernel: [    0.080839] pnp 00:01: [mem 0x000e8000-0x000ebfff window]
Jul  2 13:06:33 water kernel: [    0.080842] pnp 00:01: [mem 0x000ec000-0x000effff window]
Jul  2 13:06:33 water kernel: [    0.080846] pnp 00:01: [mem 0x60000000-0xfebfffff window]
Jul  2 13:06:33 water kernel: [    0.080925] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
Jul  2 13:06:33 water kernel: [    0.081049] pnp 00:02: [io  0x0010-0x001f]
Jul  2 13:06:33 water kernel: [    0.081052] pnp 00:02: [io  0x0090-0x009f]
Jul  2 13:06:33 water kernel: [    0.081055] pnp 00:02: [io  0x0024-0x0025]
Jul  2 13:06:33 water kernel: [    0.081058] pnp 00:02: [io  0x0028-0x0029]
Jul  2 13:06:33 water kernel: [    0.081061] pnp 00:02: [io  0x002c-0x002d]
Jul  2 13:06:33 water kernel: [    0.081065] pnp 00:02: [io  0x0030-0x0031]
Jul  2 13:06:33 water kernel: [    0.081068] pnp 00:02: [io  0x0034-0x0035]
Jul  2 13:06:33 water kernel: [    0.081071] pnp 00:02: [io  0x0038-0x0039]
Jul  2 13:06:33 water kernel: [    0.081074] pnp 00:02: [io  0x003c-0x003d]
Jul  2 13:06:33 water kernel: [    0.081077] pnp 00:02: [io  0x00a4-0x00a5]
Jul  2 13:06:33 water kernel: [    0.081080] pnp 00:02: [io  0x00a8-0x00a9]
Jul  2 13:06:33 water kernel: [    0.081083] pnp 00:02: [io  0x00ac-0x00ad]
Jul  2 13:06:33 water kernel: [    0.081086] pnp 00:02: [io  0x00b0-0x00b5]
Jul  2 13:06:33 water kernel: [    0.081089] pnp 00:02: [io  0x00b8-0x00b9]
Jul  2 13:06:33 water kernel: [    0.081092] pnp 00:02: [io  0x00bc-0x00bd]
Jul  2 13:06:33 water kernel: [    0.081095] pnp 00:02: [io  0x0050-0x0053]
Jul  2 13:06:33 water kernel: [    0.081098] pnp 00:02: [io  0x0072-0x0077]
Jul  2 13:06:33 water kernel: [    0.081101] pnp 00:02: [io  0x002e-0x002f]
Jul  2 13:06:33 water kernel: [    0.081104] pnp 00:02: [io  0x1000-0x107f]
Jul  2 13:06:33 water kernel: [    0.081107] pnp 00:02: [io  0x1180-0x11bf]
Jul  2 13:06:33 water kernel: [    0.081110] pnp 00:02: [io  0x15e0-0x15ef]
Jul  2 13:06:33 water kernel: [    0.081114] pnp 00:02: [io  0x1600-0x162f]
Jul  2 13:06:33 water kernel: [    0.081117] pnp 00:02: [io  0x1632-0x167f]
Jul  2 13:06:33 water kernel: [    0.081120] pnp 00:02: [io  0x004e-0x004f]
Jul  2 13:06:33 water kernel: [    0.081123] pnp 00:02: [io  0x1630-0x1631]
Jul  2 13:06:33 water kernel: [    0.081213] system 00:02: [io  0x1000-0x107f] has been reserved
Jul  2 13:06:33 water kernel: [    0.081217] system 00:02: [io  0x1180-0x11bf] has been reserved
Jul  2 13:06:33 water kernel: [    0.081221] system 00:02: [io  0x15e0-0x15ef] has been reserved
Jul  2 13:06:33 water kernel: [    0.081225] system 00:02: [io  0x1600-0x162f] has been reserved
Jul  2 13:06:33 water kernel: [    0.081229] system 00:02: [io  0x1632-0x167f] has been reserved
Jul  2 13:06:33 water kernel: [    0.081234] system 00:02: [io  0x1630-0x1631] has been reserved
Jul  2 13:06:33 water kernel: [    0.081238] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul  2 13:06:33 water kernel: [    0.081258] pnp 00:03: [io  0x0000-0x000f]
Jul  2 13:06:33 water kernel: [    0.081262] pnp 00:03: [io  0x0080-0x008f]
Jul  2 13:06:33 water kernel: [    0.081265] pnp 00:03: [io  0x00c0-0x00df]
Jul  2 13:06:33 water kernel: [    0.081269] pnp 00:03: [dma 4]
Jul  2 13:06:33 water kernel: [    0.081306] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Jul  2 13:06:33 water kernel: [    0.081319] pnp 00:04: [io  0x0061]
Jul  2 13:06:33 water kernel: [    0.081355] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Jul  2 13:06:33 water kernel: [    0.081368] pnp 00:05: [io  0x00f0]
Jul  2 13:06:33 water kernel: [    0.081374] pnp 00:05: [irq 13]
Jul  2 13:06:33 water kernel: [    0.081418] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Jul  2 13:06:33 water kernel: [    0.081432] pnp 00:06: [io  0x0070-0x0071]
Jul  2 13:06:33 water kernel: [    0.081435] pnp 00:06: [irq 8]
Jul  2 13:06:33 water kernel: [    0.081472] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul  2 13:06:33 water kernel: [    0.081486] pnp 00:07: [io  0x0060]
Jul  2 13:06:33 water kernel: [    0.081489] pnp 00:07: [io  0x0064]
Jul  2 13:06:33 water kernel: [    0.081492] pnp 00:07: [irq 1]
Jul  2 13:06:33 water kernel: [    0.081529] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
Jul  2 13:06:33 water kernel: [    0.081542] pnp 00:08: [irq 12]
Jul  2 13:06:33 water kernel: [    0.081581] pnp 00:08: Plug and Play ACPI device, IDs IBM0057 PNP0f13 (active)
Jul  2 13:06:33 water kernel: [    0.081628] pnp 00:09: [io  0x03f0-0x03f5]
Jul  2 13:06:33 water kernel: [    0.081631] pnp 00:09: [io  0x03f7]
Jul  2 13:06:33 water kernel: [    0.081634] pnp 00:09: [irq 6]
Jul  2 13:06:33 water kernel: [    0.081637] pnp 00:09: [dma 2]
Jul  2 13:06:33 water kernel: [    0.081700] pnp 00:09: Plug and Play ACPI device, IDs PNP0700 (active)
Jul  2 13:06:33 water kernel: [    0.081829] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (disabled)
Jul  2 13:06:33 water kernel: [    0.081954] pnp 00:0b: [io  0x03bc-0x03be]
Jul  2 13:06:33 water kernel: [    0.081957] pnp 00:0b: [irq 7]
Jul  2 13:06:33 water kernel: [    0.082051] pnp 00:0b: Plug and Play ACPI device, IDs PNP0400 (active)
Jul  2 13:06:33 water kernel: [    0.082209] pnp 00:0c: Plug and Play ACPI device, IDs IBM0071 PNP0511 (disabled)
Jul  2 13:06:33 water kernel: [    0.082924] pnp: PnP ACPI: found 13 devices
Jul  2 13:06:33 water kernel: [    0.082928] ACPI: ACPI bus type pnp unregistered
Jul  2 13:06:33 water kernel: [    0.082933] PnPBIOS: Disabled by ACPI PNP
Jul  2 13:06:33 water kernel: [    0.119875] Switching to clocksource acpi_pm
Jul  2 13:06:33 water kernel: [    0.119913] PCI: max bus depth: 2 pci_try_num: 3
Jul  2 13:06:33 water kernel: [    0.119946] pci 0000:00:1f.1: BAR 5: assigned [mem 0x60000000-0x600003ff]
Jul  2 13:06:33 water kernel: [    0.119955] pci 0000:00:1f.1: BAR 5: set to [mem 0x60000000-0x600003ff] (PCI address [0x60000000-0x600003ff])
Jul  2 13:06:33 water kernel: [    0.119962] pci 0000:01:00.0: BAR 6: assigned [mem 0xc0120000-0xc013ffff pref]
Jul  2 13:06:33 water kernel: [    0.119967] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jul  2 13:06:33 water kernel: [    0.119971] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
Jul  2 13:06:33 water kernel: [    0.119976] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
Jul  2 13:06:33 water kernel: [    0.119981] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe7ffffff pref]
Jul  2 13:06:33 water kernel: [    0.119992] pci 0000:02:00.0: BAR 15: assigned [mem 0xe8000000-0xebffffff pref]
Jul  2 13:06:33 water kernel: [    0.119996] pci 0000:02:00.0: BAR 16: assigned [mem 0xc4000000-0xc7ffffff]
Jul  2 13:06:33 water kernel: [    0.120000] pci 0000:02:00.1: BAR 15: assigned [mem 0xec000000-0xefffffff pref]
Jul  2 13:06:33 water kernel: [    0.120005] pci 0000:02:00.1: BAR 16: assigned [mem 0xc8000000-0xcbffffff]
Jul  2 13:06:33 water kernel: [    0.120010] pci 0000:02:01.0: BAR 6: assigned [mem 0xc0240000-0xc024ffff pref]
Jul  2 13:06:33 water kernel: [    0.120014] pci 0000:02:00.0: BAR 13: assigned [io  0x4000-0x40ff]
Jul  2 13:06:33 water kernel: [    0.120018] pci 0000:02:00.0: BAR 14: assigned [io  0x4400-0x44ff]
Jul  2 13:06:33 water kernel: [    0.120022] pci 0000:02:00.1: BAR 13: assigned [io  0x4800-0x48ff]
Jul  2 13:06:33 water kernel: [    0.120026] pci 0000:02:00.1: BAR 14: assigned [io  0x4c00-0x4cff]
Jul  2 13:06:33 water kernel: [    0.120030] pci 0000:02:00.0: CardBus bridge to [bus 03-06]
Jul  2 13:06:33 water kernel: [    0.120033] pci 0000:02:00.0:   bridge window [io  0x4000-0x40ff]
Jul  2 13:06:33 water kernel: [    0.120039] pci 0000:02:00.0:   bridge window [io  0x4400-0x44ff]
Jul  2 13:06:33 water kernel: [    0.120045] pci 0000:02:00.0:   bridge window [mem 0xe8000000-0xebffffff pref]
Jul  2 13:06:33 water kernel: [    0.120051] pci 0000:02:00.0:   bridge window [mem 0xc4000000-0xc7ffffff]
Jul  2 13:06:33 water kernel: [    0.120057] pci 0000:02:00.1: CardBus bridge to [bus 07-07]
Jul  2 13:06:33 water kernel: [    0.120060] pci 0000:02:00.1:   bridge window [io  0x4800-0x48ff]
Jul  2 13:06:33 water kernel: [    0.120066] pci 0000:02:00.1:   bridge window [io  0x4c00-0x4cff]
Jul  2 13:06:33 water kernel: [    0.120071] pci 0000:02:00.1:   bridge window [mem 0xec000000-0xefffffff pref]
Jul  2 13:06:33 water kernel: [    0.120077] pci 0000:02:00.1:   bridge window [mem 0xc8000000-0xcbffffff]
Jul  2 13:06:33 water kernel: [    0.120083] pci 0000:00:1e.0: PCI bridge to [bus 02-08]
Jul  2 13:06:33 water kernel: [    0.120087] pci 0000:00:1e.0:   bridge window [io  0x4000-0x8fff]
Jul  2 13:06:33 water kernel: [    0.120094] pci 0000:00:1e.0:   bridge window [mem 0xc0200000-0xcfffffff]
Jul  2 13:06:33 water kernel: [    0.120100] pci 0000:00:1e.0:   bridge window [mem 0xe8000000-0xefffffff pref]
Jul  2 13:06:33 water kernel: [    0.120123] pci 0000:00:1e.0: setting latency timer to 64
Jul  2 13:06:33 water kernel: [    0.120360] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Jul  2 13:06:33 water kernel: [    0.120365] PCI: setting IRQ 11 as level-triggered
Jul  2 13:06:33 water kernel: [    0.120372] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:06:33 water kernel: [    0.120556] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Jul  2 13:06:33 water kernel: [    0.120561] pci 0000:02:00.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:06:33 water kernel: [    0.120569] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Jul  2 13:06:33 water kernel: [    0.120573] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
Jul  2 13:06:33 water kernel: [    0.120577] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
Jul  2 13:06:33 water kernel: [    0.120581] pci_bus 0000:01: resource 1 [mem 0xc0100000-0xc01fffff]
Jul  2 13:06:33 water kernel: [    0.120585] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xe7ffffff pref]
Jul  2 13:06:33 water kernel: [    0.120589] pci_bus 0000:02: resource 0 [io  0x4000-0x8fff]
Jul  2 13:06:33 water kernel: [    0.120592] pci_bus 0000:02: resource 1 [mem 0xc0200000-0xcfffffff]
Jul  2 13:06:33 water kernel: [    0.120596] pci_bus 0000:02: resource 2 [mem 0xe8000000-0xefffffff pref]
Jul  2 13:06:33 water kernel: [    0.120600] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
Jul  2 13:06:33 water kernel: [    0.120604] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
Jul  2 13:06:33 water kernel: [    0.120608] pci_bus 0000:03: resource 0 [io  0x4000-0x40ff]
Jul  2 13:06:33 water kernel: [    0.120611] pci_bus 0000:03: resource 1 [io  0x4400-0x44ff]
Jul  2 13:06:33 water kernel: [    0.120615] pci_bus 0000:03: resource 2 [mem 0xe8000000-0xebffffff pref]
Jul  2 13:06:33 water kernel: [    0.120619] pci_bus 0000:03: resource 3 [mem 0xc4000000-0xc7ffffff]
Jul  2 13:06:33 water kernel: [    0.120623] pci_bus 0000:07: resource 0 [io  0x4800-0x48ff]
Jul  2 13:06:33 water kernel: [    0.120626] pci_bus 0000:07: resource 1 [io  0x4c00-0x4cff]
Jul  2 13:06:33 water kernel: [    0.120630] pci_bus 0000:07: resource 2 [mem 0xec000000-0xefffffff pref]
Jul  2 13:06:33 water kernel: [    0.120634] pci_bus 0000:07: resource 3 [mem 0xc8000000-0xcbffffff]
Jul  2 13:06:33 water kernel: [    0.120715] NET: Registered protocol family 2
Jul  2 13:06:33 water kernel: [    0.120818] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul  2 13:06:33 water kernel: [    0.121230] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul  2 13:06:33 water kernel: [    0.122335] Switched to NOHz mode on CPU #0
Jul  2 13:06:33 water kernel: [    0.123153] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul  2 13:06:33 water kernel: [    0.124341] TCP: Hash tables configured (established 131072 bind 65536)
Jul  2 13:06:33 water kernel: [    0.124347] TCP reno registered
Jul  2 13:06:33 water kernel: [    0.124358] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jul  2 13:06:33 water kernel: [    0.124396] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jul  2 13:06:33 water kernel: [    0.124641] NET: Registered protocol family 1
Jul  2 13:06:33 water kernel: [    0.124775] pci 0000:01:00.0: Boot video device
Jul  2 13:06:33 water kernel: [    0.124793] PCI: CLS 32 bytes, default 64
Jul  2 13:06:33 water kernel: [    0.124919] Simple Boot Flag at 0x35 set to 0x1
Jul  2 13:06:33 water kernel: [    0.125374] audit: initializing netlink socket (disabled)
Jul  2 13:06:33 water kernel: [    0.125396] type=2000 audit(1341248772.119:1): initialized
Jul  2 13:06:33 water kernel: [    0.155753] Trying to unpack rootfs image as initramfs...
Jul  2 13:06:33 water kernel: [    0.204506] highmem bounce pool size: 64 pages
Jul  2 13:06:33 water kernel: [    0.204516] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul  2 13:06:33 water kernel: [    0.236674] VFS: Disk quotas dquot_6.5.2
Jul  2 13:06:33 water kernel: [    0.236803] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul  2 13:06:33 water kernel: [    0.238041] fuse init (API version 7.16)
Jul  2 13:06:33 water kernel: [    0.238193] msgmni has been set to 1692
Jul  2 13:06:33 water kernel: [    0.252600] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul  2 13:06:33 water kernel: [    0.252646] io scheduler noop registered
Jul  2 13:06:33 water kernel: [    0.252649] io scheduler deadline registered
Jul  2 13:06:33 water kernel: [    0.252678] io scheduler cfq registered (default)
Jul  2 13:06:33 water kernel: [    0.252910] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  2 13:06:33 water kernel: [    0.252946] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul  2 13:06:33 water modem-manager[528]: <info>  ModemManager (version 0.5) starting...
Jul  2 13:06:33 water avahi-daemon[532]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Jul  2 13:06:33 water avahi-daemon[532]: Successfully dropped root privileges.
Jul  2 13:06:33 water avahi-daemon[532]: avahi-daemon 0.6.30 starting up.
Jul  2 13:06:33 water kernel: [    0.253228] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jul  2 13:06:33 water kernel: [    0.253419] ACPI: AC Adapter [AC] (on-line)
Jul  2 13:06:33 water kernel: [    0.253523] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Jul  2 13:06:33 water kernel: [    0.253695] ACPI: Lid Switch [LID]
Jul  2 13:06:33 water kernel: [    0.253757] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Jul  2 13:06:33 water kernel: [    0.253765] ACPI: Sleep Button [SLPB]
Jul  2 13:06:33 water kernel: [    0.253837] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jul  2 13:06:33 water kernel: [    0.253842] ACPI: Power Button [PWRF]
Jul  2 13:06:33 water kernel: [    0.253873] ACPI: acpi_idle registered with cpuidle
Jul  2 13:06:33 water kernel: [    0.254692] Marking TSC unstable due to TSC halts in idle
Jul  2 13:06:33 water kernel: [    0.265489] thermal LNXTHERM:00: registered as thermal_zone0
Jul  2 13:06:33 water kernel: [    0.265495] ACPI: Thermal Zone [THM0] (63 C)
Jul  2 13:06:33 water kernel: [    0.265552] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jul  2 13:06:33 water kernel: [    0.265587] ERST: Table is not found!
Jul  2 13:06:33 water kernel: [    0.265742] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul  2 13:06:33 water kernel: [    0.267479] serial 00:0a: [io  0x03f8-0x03ff]
Jul  2 13:06:33 water kernel: [    0.267539] serial 00:0a: [irq 4]
Jul  2 13:06:33 water kernel: [    0.267883] serial 00:0a: activated
Jul  2 13:06:33 water kernel: [    0.268058] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
Jul  2 13:06:33 water kernel: [    0.272265] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:06:33 water kernel: [    0.272276] serial 0000:00:1f.6: PCI INT B disabled
Jul  2 13:06:33 water kernel: [    0.272478] Linux agpgart interface v0.103
Jul  2 13:06:33 water kernel: [    0.272609] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
Jul  2 13:06:33 water kernel: [    0.286400] isapnp: Scanning for PnP cards...
Jul  2 13:06:33 water kernel: [    0.443884] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Jul  2 13:06:33 water kernel: [    0.445830] brd: module loaded
Jul  2 13:06:33 water kernel: [    0.446718] loop: module loaded
Jul  2 13:06:33 water kernel: [    0.446997] ata_piix 0000:00:1f.1: version 2.13
Jul  2 13:06:33 water kernel: [    0.447015] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
Jul  2 13:06:33 water kernel: [    0.447277] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Jul  2 13:06:33 water kernel: [    0.447285] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:06:33 water kernel: [    0.447351] ata_piix 0000:00:1f.1: setting latency timer to 64
Jul  2 13:06:33 water kernel: [    0.447826] scsi0 : ata_piix
Jul  2 13:06:33 water kernel: [    0.452162] scsi1 : ata_piix
Jul  2 13:06:33 water kernel: [    0.452885] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
Jul  2 13:06:33 water kernel: [    0.452889] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
Jul  2 13:06:33 water kernel: [    0.453526] Fixed MDIO Bus: probed
Jul  2 13:06:33 water kernel: [    0.453565] PPP generic driver version 2.4.2
Jul  2 13:06:33 water kernel: [    0.453682] tun: Universal TUN/TAP device driver, 1.6
Jul  2 13:06:33 water kernel: [    0.453685] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul  2 13:06:33 water kernel: [    0.453833] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul  2 13:06:33 water kernel: [    0.453858] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Jul  2 13:06:33 water kernel: [    0.453865] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Jul  2 13:06:33 water kernel: [    0.454076] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Jul  2 13:06:33 water kernel: [    0.454084] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:06:33 water kernel: [    0.454109] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jul  2 13:06:33 water kernel: [    0.454114] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul  2 13:06:33 water kernel: [    0.454165] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jul  2 13:06:33 water kernel: [    0.454208] ehci_hcd 0000:00:1d.7: debug port 1
Jul  2 13:06:33 water kernel: [    0.458091] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Jul  2 13:06:33 water kernel: [    0.460172] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
Jul  2 13:06:33 water kernel: [    0.480081] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jul  2 13:06:33 water kernel: [    0.480401] hub 1-0:1.0: USB hub found
Jul  2 13:06:33 water kernel: [    0.480409] hub 1-0:1.0: 6 ports detected
Jul  2 13:06:33 water kernel: [    0.480533] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul  2 13:06:33 water kernel: [    0.480561] uhci_hcd: USB Universal Host Controller Interface driver
Jul  2 13:06:33 water kernel: [    0.480658] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Jul  2 13:06:33 water kernel: [    0.480663] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Jul  2 13:06:33 water kernel: [    0.480679] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:06:33 water kernel: [    0.480693] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jul  2 13:06:33 water kernel: [    0.480698] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul  2 13:06:33 water kernel: [    0.480764] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jul  2 13:06:33 water kernel: [    0.480799] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
Jul  2 13:06:33 water kernel: [    0.480993] hub 2-0:1.0: USB hub found
Jul  2 13:06:33 water kernel: [    0.480999] hub 2-0:1.0: 2 ports detected
Jul  2 13:06:33 water kernel: [    0.481074] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Jul  2 13:06:33 water kernel: [    0.481079] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Jul  2 13:06:33 water kernel: [    0.481344] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Jul  2 13:06:33 water kernel: [    0.481350] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:06:33 water kernel: [    0.481358] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jul  2 13:06:33 water kernel: [    0.481363] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul  2 13:06:33 water kernel: [    0.481421] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jul  2 13:06:33 water kernel: [    0.481447] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
Jul  2 13:06:33 water kernel: [    0.481638] hub 3-0:1.0: USB hub found
Jul  2 13:06:33 water kernel: [    0.481643] hub 3-0:1.0: 2 ports detected
Jul  2 13:06:33 water kernel: [    0.481717] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:06:33 water kernel: [    0.481725] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jul  2 13:06:33 water kernel: [    0.481729] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul  2 13:06:33 water kernel: [    0.481777] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jul  2 13:06:33 water kernel: [    0.481801] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
Jul  2 13:06:33 water kernel: [    0.481978] hub 4-0:1.0: USB hub found
Jul  2 13:06:33 water kernel: [    0.481983] hub 4-0:1.0: 2 ports detected
Jul  2 13:06:33 water kernel: [    0.482146] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Jul  2 13:06:33 water kernel: [    0.493105] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul  2 13:06:33 water kernel: [    0.493126] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul  2 13:06:33 water kernel: [    0.496409] mousedev: PS/2 mouse device common for all mice
Jul  2 13:06:33 water kernel: [    0.496649] rtc_cmos 00:06: RTC can wake from S4
Jul  2 13:06:33 water kernel: [    0.496771] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Jul  2 13:06:33 water kernel: [    0.496794] rtc0: alarms up to one month, y3k, 114 bytes nvram
Jul  2 13:06:33 water kernel: [    0.497042] device-mapper: uevent: version 1.0.3
Jul  2 13:06:33 water kernel: [    0.497166] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
Jul  2 13:06:33 water kernel: [    0.497237] EISA: Probing bus 0 at eisa.0
Jul  2 13:06:33 water kernel: [    0.497249] Cannot allocate resource for EISA slot 1
Jul  2 13:06:33 water kernel: [    0.497254] Cannot allocate resource for EISA slot 2
Jul  2 13:06:33 water kernel: [    0.497257] Cannot allocate resource for EISA slot 3
Jul  2 13:06:33 water kernel: [    0.497260] Cannot allocate resource for EISA slot 4
Jul  2 13:06:33 water kernel: [    0.497263] Cannot allocate resource for EISA slot 5
Jul  2 13:06:33 water kernel: [    0.497265] Cannot allocate resource for EISA slot 6
Jul  2 13:06:33 water kernel: [    0.497268] Cannot allocate resource for EISA slot 7
Jul  2 13:06:33 water kernel: [    0.497271] Cannot allocate resource for EISA slot 8
Jul  2 13:06:33 water kernel: [    0.497274] EISA: Detected 0 cards.
Jul  2 13:06:33 water kernel: [    0.497290] cpufreq-nforce2: No nForce2 chipset.
Jul  2 13:06:33 water kernel: [    0.497341] cpuidle: using governor ladder
Jul  2 13:06:33 water kernel: [    0.497430] cpuidle: using governor menu
Jul  2 13:06:33 water kernel: [    0.497434] EFI Variables Facility v0.08 2004-May-17
Jul  2 13:06:33 water kernel: [    0.497899] TCP cubic registered
Jul  2 13:06:33 water kernel: [    0.498140] NET: Registered protocol family 10
Jul  2 13:06:33 water kernel: [    0.499066] NET: Registered protocol family 17
Jul  2 13:06:33 water kernel: [    0.499104] Registering the dns_resolver key type
Jul  2 13:06:33 water kernel: [    0.499134] Using IPI No-Shortcut mode
Jul  2 13:06:33 water kernel: [    0.499261] PM: Hibernation image not present or could not be loaded.
Jul  2 13:06:33 water kernel: [    0.499279] registered taskstats version 1
Jul  2 13:06:33 water kernel: [    0.506190] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul  2 13:06:33 water kernel: [    0.624525] ata2.01: NODEV after polling detection
Jul  2 13:06:33 water kernel: [    0.668024] ata1.00: HPA detected: current 151144863, native 156301488
Jul  2 13:06:33 water kernel: [    0.668033] ata1.00: ATA-6: IC25N080ATMR04-0, MO4OADEA, max UDMA/100
Jul  2 13:06:33 water kernel: [    0.668037] ata1.00: 151144863 sectors, multi 16: LBA 
Jul  2 13:06:33 water kernel: [    0.668829] ata2.00: ATAPI: UJDA745 DVD/CDRW, 1.03, max UDMA/33
Jul  2 13:06:33 water kernel: [    0.724662] ata2.00: configured for UDMA/33
Jul  2 13:06:33 water kernel: [    0.760132] ACPI: Battery Slot [BAT0] (battery present)
Jul  2 13:06:33 water kernel: [    0.816087] isapnp: No Plug & Play device found
Jul  2 13:06:33 water kernel: [    0.816806] ata1.00: configured for UDMA/100
Jul  2 13:06:33 water kernel: [    0.817030] scsi 0:0:0:0: Direct-Access     ATA      IC25N080ATMR04-0 MO4O PQ: 0 ANSI: 5
Jul  2 13:06:33 water kernel: [    0.817318] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul  2 13:06:33 water kernel: [    0.817529] sd 0:0:0:0: [sda] 151144863 512-byte logical blocks: (77.3 GB/72.0 GiB)
Jul  2 13:06:33 water kernel: [    0.817600] sd 0:0:0:0: [sda] Write Protect is off
Jul  2 13:06:33 water kernel: [    0.817604] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul  2 13:06:33 water kernel: [    0.817635] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  2 13:06:33 water kernel: [    0.859480] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA745 DVD/CDRW 1.03 PQ: 0 ANSI: 5
Jul  2 13:06:33 water kernel: [    0.863265] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jul  2 13:06:33 water kernel: [    0.863273] cdrom: Uniform CD-ROM driver Revision: 3.20
Jul  2 13:06:33 water kernel: [    0.863496] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jul  2 13:06:33 water kernel: [    0.863624] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul  2 13:06:33 water kernel: [    0.868362]  sda: sda1 sda2 < sda5 >
Jul  2 13:06:33 water kernel: [    0.868540] sda: p5 size 9762816 extends beyond EOD, enabling native capacity
Jul  2 13:06:33 water kernel: [    0.868611] ata1: soft resetting link
Jul  2 13:06:33 water kernel: [    1.040862] ata1.00: n_sectors mismatch 151144863 != 156301488
Jul  2 13:06:33 water kernel: [    1.040868] ata1.00: new n_sectors matches native, probably late HPA unlock, n_sectors updated
Jul  2 13:06:33 water kernel: [    1.057225] ata1.00: configured for UDMA/100
Jul  2 13:06:33 water kernel: [    1.057241] ata1: EH complete
Jul  2 13:06:33 water kernel: [    1.057569] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Jul  2 13:06:33 water kernel: [    1.057769] sda: detected capacity change from 77386169856 to 80026361856
Jul  2 13:06:33 water kernel: [    1.061088] Freeing initrd memory: 13292k freed
Jul  2 13:06:33 water kernel: [    1.092991]   Magic number: 4:24:137
Jul  2 13:06:33 water kernel: [    1.093048] block ram2: hash matches
Jul  2 13:06:33 water kernel: [    1.093190] rtc_cmos 00:06: setting system clock to 2012-07-02 17:06:14 UTC (1341248774)
Jul  2 13:06:33 water kernel: [    1.094231] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul  2 13:06:33 water kernel: [    1.094234] EDD information not available.
Jul  2 13:06:33 water kernel: [    1.110363]  sda: sda1 sda2 < sda5 >
Jul  2 13:06:33 water kernel: [    1.110822] sd 0:0:0:0: [sda] Attached SCSI disk
Jul  2 13:06:33 water kernel: [    1.110868] Freeing unused kernel memory: 696k freed
Jul  2 13:06:33 water kernel: [    1.111343] Write protecting the kernel text: 5332k
Jul  2 13:06:33 water kernel: [    1.111394] Write protecting the kernel read-only data: 2188k
Jul  2 13:06:33 water kernel: [    1.140088] usb 4-1: new full speed USB device number 2 using uhci_hcd
Jul  2 13:06:33 water kernel: [    1.302631] Floppy drive(s): fd0 is 1.44M
Jul  2 13:06:33 water kernel: [    1.345074] FDC 0 is a National Semiconductor PC87306
Jul  2 13:06:33 water kernel: [    1.403664] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
Jul  2 13:06:33 water kernel: [    1.403670] e1000: Copyright (c) 1999-2006 Intel Corporation.
Jul  2 13:06:33 water kernel: [    1.403732] e1000 0000:02:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:06:33 water kernel: [    1.717763] e1000 0000:02:01.0: eth0: (PCI:33MHz:32-bit) 00:0d:60:10:85:f6
Jul  2 13:06:33 water kernel: [    1.717775] e1000 0000:02:01.0: eth0: Intel(R) PRO/1000 Network Connection
Jul  2 13:06:33 water kernel: [    1.894871] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jul  2 13:06:33 water kernel: [   19.204473] lp: driver loaded but no devices found
Jul  2 13:06:33 water kernel: [   19.222965] Adding 4881404k swap on /dev/sda5.  Priority:-1 extents:1 across:4881404k 
Jul  2 13:06:33 water kernel: [   19.307098] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul  2 13:06:33 water kernel: [   19.382503] intel_rng: FWH not detected
Jul  2 13:06:33 water kernel: [   19.434166] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jul  2 13:06:33 water kernel: [   19.799203] type=1400 audit(1341248793.200:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=526 comm="apparmor_parser"
Jul  2 13:06:33 water kernel: [   19.799854] type=1400 audit(1341248793.200:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=526 comm="apparmor_parser"
Jul  2 13:06:33 water kernel: [   19.802521] type=1400 audit(1341248793.204:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=526 comm="apparmor_parser"
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin Gobi
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin X22X
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin ZTE
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin Ericsson MBM
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin Nokia
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin AnyData
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin Novatel
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin SimTech
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin Wavecom
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin MotoC
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin Sierra
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin Generic
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin Option
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin Option High-Speed
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin Huawei
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin Longcheer
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin Samsung
Jul  2 13:06:33 water modem-manager[528]: <info>  Loaded plugin Linktop
Jul  2 13:06:33 water avahi-daemon[532]: Successfully called chroot().
Jul  2 13:06:33 water avahi-daemon[532]: Successfully dropped remaining capabilities.
Jul  2 13:06:33 water avahi-daemon[532]: Loading service file /services/udisks.service.
Jul  2 13:06:33 water kernel: [   19.960177] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:0512]
Jul  2 13:06:33 water kernel: [   19.960197] yenta_cardbus 0000:02:00.0: Using INTVAL to route CSC interrupts to PCI
Jul  2 13:06:33 water kernel: [   19.960201] yenta_cardbus 0000:02:00.0: Routing CardBus interrupts to PCI
Jul  2 13:06:33 water kernel: [   19.960208] yenta_cardbus 0000:02:00.0: TI: mfunc 0x01d21022, devctl 0x64
Jul  2 13:06:33 water NetworkManager[548]: <info> NetworkManager (version 0.9.1.90) is starting...
Jul  2 13:06:33 water NetworkManager[548]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jul  2 13:06:33 water kernel: [   19.989801] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/LNXVIDEO:00/input/input4
Jul  2 13:06:33 water kernel: [   19.990760] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Jul  2 13:06:33 water kernel: [   19.993582] parport_pc 00:0b: reported by Plug and Play ACPI
Jul  2 13:06:33 water kernel: [   19.993629] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
Jul  2 13:06:33 water avahi-daemon[532]: Network interface enumeration completed.
Jul  2 13:06:33 water avahi-daemon[532]: Registering HINFO record with values 'I686'/'LINUX'.
Jul  2 13:06:33 water avahi-daemon[532]: Server startup complete. Host name is water.local. Local service cookie is 1643132491.
Jul  2 13:06:33 water avahi-daemon[532]: Service "water" (/services/udisks.service) successfully established.
Jul  2 13:06:33 water NetworkManager[548]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jul  2 13:06:33 water kernel: [   20.042316] cfg80211: Calling CRDA to update world regulatory domain
Jul  2 13:06:33 water dbus[512]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jul  2 13:06:33 water kernel: [   20.113101] Non-volatile memory driver v1.3
Jul  2 13:06:33 water polkitd[558]: started daemon version 0.102 using authority implementation `local' version `0.102'
Jul  2 13:06:33 water dbus[512]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jul  2 13:06:33 water kernel: [   20.202939] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x0438, PCI irq 11
Jul  2 13:06:33 water kernel: [   20.202946] yenta_cardbus 0000:02:00.0: Socket status: 30000006
Jul  2 13:06:33 water kernel: [   20.202959] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge window: [io  0x4000-0x8fff]
Jul  2 13:06:33 water NetworkManager[548]:    SCPlugin-Ifupdown: init!
Jul  2 13:06:33 water NetworkManager[548]:    SCPlugin-Ifupdown: update_system_hostname
Jul  2 13:06:33 water NetworkManager[548]:    SCPluginIfupdown: management mode: unmanaged
Jul  2 13:06:33 water NetworkManager[548]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0)
Jul  2 13:06:33 water NetworkManager[548]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul  2 13:06:33 water NetworkManager[548]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul  2 13:06:33 water NetworkManager[548]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul  2 13:06:33 water NetworkManager[548]:    SCPlugin-Ifupdown: end _init.
Jul  2 13:06:33 water NetworkManager[548]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul  2 13:06:33 water NetworkManager[548]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul  2 13:06:33 water NetworkManager[548]:    Ifupdown: get unmanaged devices count: 0
Jul  2 13:06:33 water NetworkManager[548]:    SCPlugin-Ifupdown: (162703504) ... get_connections.
Jul  2 13:06:33 water NetworkManager[548]:    SCPlugin-Ifupdown: (162703504) ... get_connections (managed=false): return empty list.
Jul  2 13:06:33 water NetworkManager[548]:    keyfile: parsing cabin ... 
Jul  2 13:06:33 water kernel: [   20.202965] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x8fff: excluding 0x4000-0x40ff 0x4400-0x44ff 0x4800-0x48ff 0x4c00-0x4cff
Jul  2 13:06:33 water kernel: [   20.252301] lp0: using parport0 (interrupt-driven).
Jul  2 13:06:33 water kernel: [   20.254060] irda_init()
Jul  2 13:06:33 water kernel: [   20.254083] NET: Registered protocol family 23
Jul  2 13:06:33 water kernel: [   20.255359] nsc-ircc 00:0c: [io  0x02f8-0x02ff]
Jul  2 13:06:33 water kernel: [   20.255427] nsc-ircc 00:0c: [irq 3]
Jul  2 13:06:33 water kernel: [   20.255433] nsc-ircc 00:0c: [dma 1]
Jul  2 13:06:33 water kernel: [   20.255893] nsc-ircc 00:0c: activated
Jul  2 13:06:33 water kernel: [   20.255898] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
Jul  2 13:06:33 water NetworkManager[548]:    keyfile:     read connection 'cabin'
Jul  2 13:06:33 water NetworkManager[548]:    Ifupdown: get unmanaged devices count: 0
Jul  2 13:06:33 water NetworkManager[548]: <info> modem-manager is now available
Jul  2 13:06:33 water NetworkManager[548]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul  2 13:06:33 water kernel: [   20.299041] nsc-ircc, chip->init
Jul  2 13:06:33 water kernel: [   20.299055] nsc-ircc, Found chip at base=0x02e
Jul  2 13:06:33 water kernel: [   20.299080] nsc-ircc, driver loaded (Dag Brattli)
Jul  2 13:06:33 water kernel: [   20.300522] [drm] Initialized drm 1.1.0 20060810
Jul  2 13:06:33 water kernel: [   20.313044] IrDA: Registered device irda0
Jul  2 13:06:33 water kernel: [   20.313051] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
Jul  2 13:06:33 water NetworkManager[548]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul  2 13:06:33 water NetworkManager[548]: <info> WWAN enabled by radio killswitch; enabled by state file
Jul  2 13:06:33 water NetworkManager[548]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul  2 13:06:33 water NetworkManager[548]: <info> Networking is enabled by state file
Jul  2 13:06:33 water NetworkManager[548]: <info> (eth0): carrier is OFF
Jul  2 13:06:33 water NetworkManager[548]: <info> (eth0): new Ethernet device (driver: 'e1000' ifindex: 2)
Jul  2 13:06:33 water NetworkManager[548]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul  2 13:06:33 water NetworkManager[548]: <info> (eth0): now managed
Jul  2 13:06:33 water NetworkManager[548]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul  2 13:06:33 water NetworkManager[548]: <info> (eth0): bringing up device.
Jul  2 13:06:33 water kernel: [   20.435697] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  2 13:06:33 water NetworkManager[548]: <info> (eth0): preparing device.
Jul  2 13:06:33 water NetworkManager[548]: <info> (eth0): deactivating device (reason 'managed') [2]
Jul  2 13:06:33 water NetworkManager[548]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0
Jul  2 13:06:33 water NetworkManager[548]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jul  2 13:06:33 water kernel: [   20.465083] Bluetooth: Core ver 2.16
Jul  2 13:06:33 water kernel: [   20.472061] NET: Registered protocol family 31
Jul  2 13:06:33 water kernel: [   20.472067] Bluetooth: HCI device and connection manager initialized
Jul  2 13:06:33 water kernel: [   20.472072] Bluetooth: HCI socket layer initialized
Jul  2 13:06:33 water kernel: [   20.472075] Bluetooth: L2CAP socket layer initialized
Jul  2 13:06:33 water kernel: [   20.474292] Bluetooth: SCO socket layer initialized
Jul  2 13:06:33 water kernel: [   20.520507] Bluetooth: Generic Bluetooth USB driver ver 0.6
Jul  2 13:06:33 water NetworkManager[548]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0)
Jul  2 13:06:33 water NetworkManager[548]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul  2 13:06:33 water kernel: [   20.551794]  0x8000-0x803f
Jul  2 13:06:33 water kernel: [   20.564400] usbcore: registered new interface driver btusb
Jul  2 13:06:34 water kernel: [   20.614282] 
Jul  2 13:06:34 water kernel: [   20.614294] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge window: [mem 0xc0200000-0xcfffffff]
Jul  2 13:06:34 water kernel: [   20.614301] pcmcia_socket pcmcia_socket0: cs: memory probe 0xc0200000-0xcfffffff: excluding 0xc0200000-0xc09fffff 0xc3a00000-0xcc1fffff 0xcfa00000-0xd01fffff
Jul  2 13:06:34 water kernel: [   20.614331] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge window: [mem 0xe8000000-0xefffffff pref]
Jul  2 13:06:34 water kernel: [   20.614335] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe8000000-0xefffffff: excluding 0xe8000000-0xefffffff
Jul  2 13:06:34 water kernel: [   20.649831] yenta_cardbus 0000:02:00.1: CardBus bridge found [1014:0512]
Jul  2 13:06:34 water kernel: [   20.649851] yenta_cardbus 0000:02:00.1: Using INTVAL to route CSC interrupts to PCI
Jul  2 13:06:34 water kernel: [   20.649855] yenta_cardbus 0000:02:00.1: Routing CardBus interrupts to PCI
Jul  2 13:06:34 water kernel: [   20.649862] yenta_cardbus 0000:02:00.1: TI: mfunc 0x01d21022, devctl 0x64
Jul  2 13:06:34 water NetworkManager[548]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul  2 13:06:34 water NetworkManager[548]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul  2 13:06:34 water failsafe: Failsafe of 120 seconds reached.
Jul  2 13:06:34 water kernel: [   20.880679] yenta_cardbus 0000:02:00.1: ISA IRQ mask 0x0438, PCI irq 11
Jul  2 13:06:34 water kernel: [   20.880686] yenta_cardbus 0000:02:00.1: Socket status: 30000006
Jul  2 13:06:34 water kernel: [   20.880698] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge window: [io  0x4000-0x8fff]
Jul  2 13:06:34 water kernel: [   20.880704] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x8fff: excluding 0x4000-0x40ff 0x4400-0x44ff 0x4800-0x48ff 0x4c00-0x4cff
Jul  2 13:06:34 water kernel: [   21.049930] type=1400 audit(1341248794.452:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=718 comm="apparmor_parser"
Jul  2 13:06:34 water kernel: [   21.057846] type=1400 audit(1341248794.460:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=722 comm="apparmor_parser"
Jul  2 13:06:34 water kernel: [   21.059536] type=1400 audit(1341248794.460:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=722 comm="apparmor_parser"
Jul  2 13:06:34 water kernel: [   21.059971] type=1400 audit(1341248794.460:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=722 comm="apparmor_parser"
Jul  2 13:06:34 water kernel: [   21.106639] type=1400 audit(1341248794.508:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=723 comm="apparmor_parser"
Jul  2 13:06:34 water kernel: [   21.112336] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0/0x0
Jul  2 13:06:34 water kernel: [   21.112346] serio: Synaptics pass-through port at isa0060/serio1/input0
Jul  2 13:06:34 water kernel: [   21.116835] [drm] radeon defaulting to kernel modesetting.
Jul  2 13:06:34 water kernel: [   21.116840] [drm] radeon kernel modesetting enabled.
Jul  2 13:06:34 water kernel: [   21.116977] radeon 0000:01:00.0: power state changed by ACPI to D0
Jul  2 13:06:34 water kernel: [   21.116983] radeon 0000:01:00.0: power state changed by ACPI to D0
Jul  2 13:06:34 water kernel: [   21.116997] radeon 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:06:34 water kernel: [   21.131579] type=1400 audit(1341248794.532:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=723 comm="apparmor_parser"
Jul  2 13:06:34 water kernel: [   21.143517] type=1400 audit(1341248794.544:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=723 comm="apparmor_parser"
Jul  2 13:06:34 water kernel: [   21.151833] [drm] initializing kernel modesetting (RV250 0x1002:0x4C66 0x1014:0x0531).
Jul  2 13:06:34 water kernel: [   21.151879] [drm] register mmio base: 0xC0100000
Jul  2 13:06:34 water kernel: [   21.151881] [drm] register mmio size: 65536
Jul  2 13:06:34 water kernel: [   21.152251] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
Jul  2 13:06:34 water kernel: [   21.152914] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
Jul  2 13:06:34 water kernel: [   21.173098] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
Jul  2 13:06:34 water kernel: [   21.173142] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
Jul  2 13:06:34 water kernel: [   21.173174] radeon 0000:01:00.0: GTT: 256M 0xD0000000 - 0xDFFFFFFF
Jul  2 13:06:34 water kernel: [   21.173186] radeon 0000:01:00.0: VRAM: 128M 0x00000000E0000000 - 0x00000000E7FFFFFF (32M used)
Jul  2 13:06:34 water kernel: [   21.173207] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jul  2 13:06:34 water kernel: [   21.173209] [drm] Driver supports precise vblank timestamp query.
Jul  2 13:06:34 water kernel: [   21.173232] [drm] radeon: irq initialized.
Jul  2 13:06:34 water kernel: [   21.182808]  0x8000-0x803f
Jul  2 13:06:34 water kernel: [   21.194582] [drm] Detected VRAM RAM=128M, BAR=128M
Jul  2 13:06:34 water kernel: [   21.194588] [drm] RAM width 64bits DDR
Jul  2 13:06:34 water kernel: [   21.200928] thinkpad_acpi: ThinkPad ACPI Extras v0.24
Jul  2 13:06:34 water kernel: [   21.200933] thinkpad_acpi: http://ibm-acpi.sf.net/
Jul  2 13:06:34 water kernel: [   21.200936] thinkpad_acpi: ThinkPad BIOS 1RETDMWW (3.18 ), EC 1RHT71WW-3.04
Jul  2 13:06:34 water kernel: [   21.200939] thinkpad_acpi: IBM ThinkPad T40 , model 237392U
Jul  2 13:06:34 water kernel: [   21.200942] thinkpad_acpi: WARNING: Outdated ThinkPad BIOS/EC firmware
Jul  2 13:06:34 water kernel: [   21.200945] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
Jul  2 13:06:34 water kernel: [   21.201201] [TTM] Zone  kernel: Available graphics memory: 440360 kiB.
Jul  2 13:06:34 water kernel: [   21.201204] [TTM] Zone highmem: Available graphics memory: 771820 kiB.
Jul  2 13:06:34 water kernel: [   21.201207] [TTM] Initializing pool allocator.
Jul  2 13:06:34 water kernel: [   21.201252] [drm] radeon: 32M of VRAM memory ready
Jul  2 13:06:34 water kernel: [   21.201259] [drm] radeon: 256M of GTT memory ready.
Jul  2 13:06:34 water kernel: [   21.202589] radeon 0000:01:00.0: WB disabled
Jul  2 13:06:34 water kernel: [   21.240890] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
Jul  2 13:06:34 water kernel: [   21.242384] [drm] Loading R200 Microcode
Jul  2 13:06:34 water kernel: [   21.283014] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
Jul  2 13:06:34 water kernel: [   21.285109] Registered led device: tpacpi::thinklight
Jul  2 13:06:34 water kernel: [   21.303352] Registered led device: tpacpi::power
Jul  2 13:06:34 water kernel: [   21.307665] Registered led device: tpacpi::standby
Jul  2 13:06:34 water udev-configure-printer: add /module/lp
Jul  2 13:06:34 water udev-configure-printer: Failed to get parent
Jul  2 13:06:34 water kernel: [   21.337495] 
Jul  2 13:06:34 water kernel: [   21.337507] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge window: [mem 0xc0200000-0xcfffffff]
Jul  2 13:06:34 water kernel: [   21.337514] pcmcia_socket pcmcia_socket1: cs: memory probe 0xc0200000-0xcfffffff: excluding 0xc0200000-0xc09fffff 0xc3a00000-0xcc1fffff 0xcfa00000-0xd01fffff
Jul  2 13:06:34 water kernel: [   21.337544] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge window: [mem 0xe8000000-0xefffffff pref]
Jul  2 13:06:34 water kernel: [   21.337548] pcmcia_socket pcmcia_socket1: cs: memory probe 0xe8000000-0xefffffff: excluding 0xe8000000-0xefffffff
Jul  2 13:06:34 water kernel: [   21.348156] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
Jul  2 13:06:34 water kernel: [   21.352679] ath5k 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:06:35 water acpid: starting up with proc fs
Jul  2 13:06:35 water acpid: 32 rules loaded
Jul  2 13:06:35 water acpid: waiting for events: event logging is off
Jul  2 13:06:35 water cron[801]: (CRON) INFO (pidfile fd = 3)
Jul  2 13:06:35 water anacron[824]: Anacron 2.3 started on 2012-07-02
Jul  2 13:06:35 water cron[826]: (CRON) STARTUP (fork ok)
Jul  2 13:06:35 water cron[826]: (CRON) INFO (Running @reboot jobs)
Jul  2 13:06:35 water anacron[824]: Will run job `cron.daily' in 5 min.
Jul  2 13:06:35 water anacron[824]: Will run job `cron.weekly' in 10 min.
Jul  2 13:06:35 water anacron[824]: Jobs will be executed sequentially
Jul  2 13:06:35 water NetworkManager[548]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/irda0, iface: irda0)
Jul  2 13:06:35 water NetworkManager[548]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/irda0, iface: irda0): no ifupdown configuration found.
Jul  2 13:06:35 water udev-configure-printer: add /devices/pnp0/00:0b/printer/lp0
Jul  2 13:06:35 water bluetoothd[878]: Bluetooth daemon 4.96
Jul  2 13:06:35 water NetworkManager[548]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/ieee80211/phy0/rfkill2) (driver (unknown))
Jul  2 13:06:35 water udev-configure-printer: Failed to get parent
Jul  2 13:06:35 water kernel: [   21.352759] ath5k 0000:02:02.0: registered as 'phy0'
Jul  2 13:06:35 water kernel: [   21.617693] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:06:35 water kernel: [   21.617733] Intel ICH 0000:00:1f.5: setting latency timer to 64
Jul  2 13:06:35 water kernel: [   21.651758] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
Jul  2 13:06:35 water kernel: [   21.718782] init: failsafe main process (660) killed by TERM signal
Jul  2 13:06:35 water kernel: [   21.731114] init: apport pre-start process (791) terminated with status 1
Jul  2 13:06:35 water kernel: [   21.767407] ath: EEPROM regdomain: 0x61
Jul  2 13:06:35 water kernel: [   21.767413] ath: EEPROM indicates we should expect a direct regpair map
Jul  2 13:06:35 water kernel: [   21.767420] ath: Country alpha2 being used: 00
Jul  2 13:06:35 water kernel: [   21.767422] ath: Regpair used: 0x61
Jul  2 13:06:35 water kernel: [   21.767428] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767432] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   21.767436] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767440] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   21.767444] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767448] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   21.767451] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767455] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   21.767459] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water bluetoothd[878]: Starting SDP server
Jul  2 13:06:35 water kernel: [   21.767463] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   21.767467] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767471] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   21.767474] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767479] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   21.767482] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767486] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   21.767490] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767494] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   21.767497] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767502] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   21.767505] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767509] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   21.767513] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767517] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   21.767520] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767525] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   21.767528] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767532] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   21.767536] cfg80211: Disabling freq 5040 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jul  2 13:06:35 water kernel: [   21.767540] cfg80211: Disabling freq 5060 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jul  2 13:06:35 water kernel: [   21.767544] cfg80211: Disabling freq 5080 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jul  2 13:06:35 water kernel: [   21.767547] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767552] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767555] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767559] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767563] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767567] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767571] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767575] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767579] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767583] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767586] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767590] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767594] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767598] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767602] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767622] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767626] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767630] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767634] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767638] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767641] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767646] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767649] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767653] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767657] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767661] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767665] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767669] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767672] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767677] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767680] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767684] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767688] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767692] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767696] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767700] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767703] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767708] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767711] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767715] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767719] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767723] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767727] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767731] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767734] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767739] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.767742] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:06:35 water kernel: [   21.767746] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:06:35 water kernel: [   21.776765] init: apport post-stop process (823) terminated with status 1
Jul  2 13:06:35 water kernel: [   21.809356] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Jul  2 13:06:35 water kernel: [   21.855327] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jul  2 13:06:35 water kernel: [   21.876456] Registered led device: ath5k-phy0::rx
Jul  2 13:06:35 water kernel: [   21.876521] Registered led device: ath5k-phy0::tx
Jul  2 13:06:35 water kernel: [   21.876537] ath5k phy0: Atheros AR5211 chip found (MAC: 0x42, PHY: 0x30)
Jul  2 13:06:35 water kernel: [   21.876540] ath5k phy0: RF5111 5GHz radio found (0x17)
Jul  2 13:06:35 water kernel: [   21.876543] ath5k phy0: RF2111 2GHz radio found (0x23)
Jul  2 13:06:35 water kernel: [   22.030500] ppdev: user-space parallel port driver
Jul  2 13:06:35 water kernel: [   22.046815] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Jul  2 13:06:35 water kernel: [   22.046822] cfg80211: World regulatory domain updated:
Jul  2 13:06:35 water kernel: [   22.046825] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul  2 13:06:35 water kernel: [   22.046830] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   22.046834] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   22.046838] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   22.046842] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   22.046846] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:06:35 water kernel: [   22.148766] Bluetooth: RFCOMM TTY layer initialized
Jul  2 13:06:35 water kernel: [   22.148776] Bluetooth: RFCOMM socket layer initialized
Jul  2 13:06:35 water kernel: [   22.148779] Bluetooth: RFCOMM ver 1.11
Jul  2 13:06:35 water kernel: [   22.163707] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377
Jul  2 13:06:35 water kernel: [   22.168444] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
Jul  2 13:06:35 water kernel: [   22.168905] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Jul  2 13:06:35 water kernel: [   22.169298] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Jul  2 13:06:35 water kernel: [   22.169724] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xdc000-0xfffff
Jul  2 13:06:35 water kernel: [   22.169793] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Jul  2 13:06:35 water kernel: [   22.169861] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x600fffff
Jul  2 13:06:35 water kernel: [   22.209492] [drm] radeon: ring at 0x00000000D0001000
Jul  2 13:06:35 water kernel: [   22.209517] [drm] ring test succeeded in 1 usecs
Jul  2 13:06:35 water kernel: [   22.209821] [drm] radeon: ib pool ready.
Jul  2 13:06:35 water kernel: [   22.209942] [drm] ib test succeeded in 0 usecs
Jul  2 13:06:35 water kernel: [   22.211920] [drm] Panel ID String: SXGA+ Single (85MHz)    
Jul  2 13:06:35 water kernel: [   22.211925] [drm] Panel Size 1400x1050
Jul  2 13:06:35 water kernel: [   22.223094] [drm] radeon legacy LVDS backlight initialized
Jul  2 13:06:35 water kernel: [   22.229257] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Jul  2 13:06:35 water kernel: [   22.232996] [drm] No TV DAC info found in BIOS
Jul  2 13:06:35 water kernel: [   22.234428] [drm] Radeon Display Connectors
Jul  2 13:06:35 water kernel: [   22.234432] [drm] Connector 0:
Jul  2 13:06:35 water kernel: [   22.234435] [drm]   VGA
Jul  2 13:06:35 water kernel: [   22.234439] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
Jul  2 13:06:35 water kernel: [   22.234442] [drm]   Encoders:
Jul  2 13:06:35 water kernel: [   22.234444] [drm]     CRT1: INTERNAL_DAC1
Jul  2 13:06:35 water kernel: [   22.234447] [drm] Connector 1:
Jul  2 13:06:35 water kernel: [   22.234449] [drm]   DVI-D
Jul  2 13:06:35 water kernel: [   22.234451] [drm]   HPD1
Jul  2 13:06:35 water kernel: [   22.234454] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Jul  2 13:06:35 water kernel: [   22.234456] [drm]   Encoders:
Jul  2 13:06:35 water kernel: [   22.234459] [drm]     DFP1: INTERNAL_TMDS1
Jul  2 13:06:35 water kernel: [   22.234461] [drm] Connector 2:
Jul  2 13:06:35 water kernel: [   22.234463] [drm]   LVDS
Jul  2 13:06:35 water kernel: [   22.234465] [drm]   Encoders:
Jul  2 13:06:35 water kernel: [   22.234467] [drm]     LCD1: INTERNAL_LVDS
Jul  2 13:06:35 water kernel: [   22.234469] [drm] Connector 3:
Jul  2 13:06:35 water kernel: [   22.234471] [drm]   S-video
Jul  2 13:06:35 water kernel: [   22.234473] [drm]   Encoders:
Jul  2 13:06:35 water kernel: [   22.234475] [drm]     TV1: INTERNAL_DAC2
Jul  2 13:06:35 water bluetoothd[878]: Listening for HCI events on hci0
Jul  2 13:06:35 water bluetoothd[878]: HCI dev 0 up
Jul  2 13:06:35 water NetworkManager[548]: <warn> bluez error getting default adapter: No such adapter
Jul  2 13:06:35 water kernel: [   22.267707] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377
Jul  2 13:06:35 water kernel: [   22.332462] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
Jul  2 13:06:35 water kernel: [   22.332924] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
Jul  2 13:06:35 water kernel: [   22.333317] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
Jul  2 13:06:35 water kernel: [   22.333748] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xdc000-0xfffff
Jul  2 13:06:35 water kernel: [   22.333817] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Jul  2 13:06:35 water kernel: [   22.333887] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x600fffff
Jul  2 13:06:35 water kernel: [   22.333962] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
Jul  2 13:06:35 water kernel: [   22.334505] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul  2 13:06:35 water kernel: [   22.334508] Bluetooth: BNEP filters: protocol multicast
Jul  2 13:06:35 water bluetoothd[878]: Adapter /org/bluez/878/hci0 has been enabled
Jul  2 13:06:35 water bluetoothd[878]: Inquiry Cancel Failed with status 0x0c
Jul  2 13:06:35 water NetworkManager[548]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jul  2 13:06:35 water NetworkManager[548]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 4)
Jul  2 13:06:35 water NetworkManager[548]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul  2 13:06:35 water NetworkManager[548]: <info> (wlan0): now managed
Jul  2 13:06:35 water NetworkManager[548]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul  2 13:06:35 water NetworkManager[548]: <info> (wlan0): bringing up device.
Jul  2 13:06:35 water NetworkManager[548]: <info> (wlan0): preparing device.
Jul  2 13:06:35 water NetworkManager[548]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jul  2 13:06:35 water kernel: [   22.462711] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
Jul  2 13:06:35 water kernel: [   22.521610] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  2 13:06:35 water dbus[512]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jul  2 13:06:35 water NetworkManager[548]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wlan0, iface: wlan0)
Jul  2 13:06:35 water NetworkManager[548]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul  2 13:06:35 water kernel: [   22.551554] [drm] Radeon display connector DVI-D-1: No monitor connected or invalid EDID
Jul  2 13:06:35 water dbus[512]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jul  2 13:06:35 water NetworkManager[548]: <info> wpa_supplicant started
Jul  2 13:06:36 water kernel: [   22.551596] [drm] radeon: power management initialized
Jul  2 13:06:36 water kernel: [   22.608276] [drm] fb mappable at 0xE0040000
Jul  2 13:06:36 water kernel: [   22.608281] [drm] vram apper at 0xE0000000
Jul  2 13:06:36 water kernel: [   22.608284] [drm] size 1478656
Jul  2 13:06:36 water kernel: [   22.608286] [drm] fb depth is 8
Jul  2 13:06:36 water kernel: [   22.608288] [drm]    pitch is 1408
Jul  2 13:06:36 water kernel: [   22.611226] fbcon: radeondrmfb (fb0) is primary device
Jul  2 13:06:36 water kernel: [   22.612875] Console: switching to colour frame buffer device 175x65
Jul  2 13:06:36 water kernel: [   22.612950] fb0: radeondrmfb frame buffer device
Jul  2 13:06:36 water kernel: [   22.612953] drm: registered panic notifier
Jul  2 13:06:36 water kernel: [   22.612968] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:00.0 on minor 0
Jul  2 13:06:36 water kernel: [   22.704438] intel8x0_measure_ac97_clock: measured 54682 usecs (2635 samples)
Jul  2 13:06:36 water kernel: [   22.704444] intel8x0: clocking to 48000
Jul  2 13:06:36 water NetworkManager[548]: <info> (wlan0): supplicant interface state: starting -> ready
Jul  2 13:06:36 water NetworkManager[548]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul  2 13:06:36 water NetworkManager[548]: <info> (wlan0): supplicant interface state: ready -> inactive
Jul  2 13:06:37 water acpid: client connected from 1019[0:0]
Jul  2 13:06:37 water acpid: 1 client rule loaded
Jul  2 13:06:37 water kernel: [   23.821635] psmouse serio2: ID: 10 00 64
Jul  2 13:06:37 water dbus[512]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jul  2 13:06:37 water udev-configure-printer: add /devices/pnp0/00:0b/printer/lp0
Jul  2 13:06:37 water dbus[512]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jul  2 13:06:37 water udev-configure-printer: Failed to get parent
Jul  2 13:06:37 water udev-configure-printer: add /module/lp
Jul  2 13:06:37 water udev-configure-printer: Failed to get parent
Jul  2 13:06:37 water accounts-daemon[1026]: started daemon version 0.6.14
Jul  2 13:06:37 water dbus[512]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jul  2 13:06:38 water dbus[512]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jul  2 13:06:38 water dbus[512]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jul  2 13:06:38 water dbus[512]: [system] Successfully activated service 'org.freedesktop.UPower'
Jul  2 13:06:39 water dbus[512]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jul  2 13:06:39 water dbus[512]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jul  2 13:06:40 water dbus[512]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jul  2 13:06:40 water dbus[512]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jul  2 17:06:40 water rtkit-daemon[1212]: Successfully called chroot.
Jul  2 17:06:40 water rtkit-daemon[1212]: Successfully dropped privileges.
Jul  2 17:06:40 water rtkit-daemon[1212]: Successfully limited resources.
Jul  2 17:06:40 water rtkit-daemon[1212]: Running.
Jul  2 17:06:40 water rtkit-daemon[1212]: Watchdog thread running.
Jul  2 17:06:40 water rtkit-daemon[1212]: Canary thread running.
Jul  2 17:06:40 water rtkit-daemon[1212]: Successfully made thread 1210 of process 1210 (n/a) owned by '104' high priority at nice level -11.
Jul  2 17:06:40 water rtkit-daemon[1212]: Supervising 1 threads of 1 processes of 1 users.
Jul  2 13:06:40 water kernel: [   27.158201] IBM TrackPoint firmware: 0x0e, buttons: 3/3
Jul  2 17:06:40 water rtkit-daemon[1212]: Successfully made thread 1217 of process 1210 (n/a) owned by '104' RT at priority 5.
Jul  2 17:06:40 water rtkit-daemon[1212]: Supervising 2 threads of 1 processes of 1 users.
Jul  2 17:06:40 water rtkit-daemon[1212]: Successfully made thread 1218 of process 1210 (n/a) owned by '104' RT at priority 5.
Jul  2 17:06:40 water rtkit-daemon[1212]: Supervising 3 threads of 1 processes of 1 users.
Jul  2 13:06:40 water pulseaudio[1210]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Jul  2 13:06:40 water pulseaudio[1210]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Jul  2 13:06:40 water pulseaudio[1210]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Jul  2 13:06:40  pulseaudio[1210]: last message repeated 2 times
Jul  2 13:06:40 water kernel: [   27.376854] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input7
Jul  2 13:06:45 water kernel: [   31.619849] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jul  2 13:06:45 water kernel: [   31.965541] init: plymouth-stop pre-start process (1262) terminated with status 1
Jul  2 13:11:35 water anacron[824]: Job `cron.daily' started
Jul  2 13:11:35 water anacron[1269]: Updated timestamp for job `cron.daily' to 2012-07-02
Jul  2 13:11:53 water gnome-session[1353]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1
Jul  2 17:11:55 water rtkit-daemon[1212]: Successfully made thread 1440 of process 1440 (n/a) owned by '1000' high priority at nice level -11.
Jul  2 17:11:55 water rtkit-daemon[1212]: Supervising 4 threads of 2 processes of 2 users.
Jul  2 17:11:55 water rtkit-daemon[1212]: Successfully made thread 1441 of process 1440 (n/a) owned by '1000' RT at priority 5.
Jul  2 17:11:55 water rtkit-daemon[1212]: Supervising 5 threads of 2 processes of 2 users.
Jul  2 17:11:55 water rtkit-daemon[1212]: Successfully made thread 1442 of process 1440 (n/a) owned by '1000' RT at priority 5.
Jul  2 17:11:55 water rtkit-daemon[1212]: Supervising 6 threads of 2 processes of 2 users.
Jul  2 13:11:55 water pulseaudio[1440]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Jul  2 13:11:55 water pulseaudio[1440]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Jul  2 13:11:55 water pulseaudio[1440]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Jul  2 13:11:56  pulseaudio[1440]: last message repeated 2 times
Jul  2 13:11:56 water dbus[512]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jul  2 13:11:56 water dbus[512]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jul  2 13:13:04 water dbus[512]: [system] Activating service name='com.ubuntu.SystemService' (using servicehelper)
Jul  2 13:13:05 water dbus[512]: [system] Successfully activated service 'com.ubuntu.SystemService'
Jul  2 13:13:23 water dbus[512]: [system] Activating service name='org.debian.apt' (using servicehelper)
Jul  2 13:13:25 water AptDaemon: INFO: Initializing daemon
Jul  2 13:13:25 water dbus[512]: [system] Successfully activated service 'org.debian.apt'
Jul  2 13:13:25 water AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Jul  2 13:13:25 water AptDaemon.Trans: INFO: Simulate was called
Jul  2 13:13:25 water AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/70a37912dd6948ed91d0be536c62e1bc
Jul  2 13:13:30 water AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Jul  2 13:17:01 water CRON[2554]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 13:17:17 water kernel: [  664.352113] Critical temperature reached (93 C), shutting down.
Jul  2 13:17:17 water kernel: Kernel logging (proc) stopped.
Jul  2 13:17:17 water rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="509" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jul  2 13:21:15 water kernel: imklog 5.8.1, log source = /proc/kmsg started.
Jul  2 13:21:15 water rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="494" x-info="http://www.rsyslog.com"] start
Jul  2 13:21:15 water rsyslogd: rsyslogd's groupid changed to 103
Jul  2 13:21:15 water rsyslogd: rsyslogd's userid changed to 101
Jul  2 13:21:15 water rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul  2 13:21:15 water kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  2 13:21:15 water kernel: [    0.000000] Initializing cgroup subsys cpu
Jul  2 13:21:15 water kernel: [    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
Jul  2 13:21:15 water kernel: [    0.000000] KERNEL supported cpus:
Jul  2 13:21:15 water kernel: [    0.000000]   Intel GenuineIntel
Jul  2 13:21:15 water kernel: [    0.000000]   AMD AuthenticAMD
Jul  2 13:21:15 water kernel: [    0.000000]   NSC Geode by NSC
Jul  2 13:21:15 water kernel: [    0.000000]   Cyrix CyrixInstead
Jul  2 13:21:15 water kernel: [    0.000000]   Centaur CentaurHauls
Jul  2 13:21:15 water kernel: [    0.000000]   Transmeta GenuineTMx86
Jul  2 13:21:15 water kernel: [    0.000000]   Transmeta TransmetaCPU
Jul  2 13:21:15 water kernel: [    0.000000]   UMC UMC UMC UMC
Jul  2 13:21:15 water kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  2 13:21:15 water kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jul  2 13:21:15 water kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jul  2 13:21:15 water kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Jul  2 13:21:15 water kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Jul  2 13:21:15 water kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000005ff60000 (usable)
Jul  2 13:21:15 water kernel: [    0.000000]  BIOS-e820: 000000005ff60000 - 000000005ff77000 (ACPI data)
Jul  2 13:21:15 water kernel: [    0.000000]  BIOS-e820: 000000005ff77000 - 000000005ff79000 (ACPI NVS)
Jul  2 13:21:15 water kernel: [    0.000000]  BIOS-e820: 000000005ff80000 - 0000000060000000 (reserved)
Jul  2 13:21:15 water kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
Jul  2 13:21:15 water kernel: [    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
Jul  2 13:21:15 water kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Jul  2 13:21:15 water kernel: [    0.000000] DMI present.
Jul  2 13:21:15 water kernel: [    0.000000] DMI: IBM 237392U/237392U, BIOS 1RETDMWW (3.18 ) 09/15/2005
Jul  2 13:21:15 water kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jul  2 13:21:15 water kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jul  2 13:21:15 water kernel: [    0.000000] last_pfn = 0x5ff60 max_arch_pfn = 0x100000
Jul  2 13:21:15 water kernel: [    0.000000] MTRR default type: uncachable
Jul  2 13:21:15 water kernel: [    0.000000] MTRR fixed ranges enabled:
Jul  2 13:21:15 water kernel: [    0.000000]   00000-9FFFF write-back
Jul  2 13:21:15 water kernel: [    0.000000]   A0000-BFFFF uncachable
Jul  2 13:21:15 water kernel: [    0.000000]   C0000-CFFFF write-protect
Jul  2 13:21:15 water kernel: [    0.000000]   D0000-DBFFF uncachable
Jul  2 13:21:15 water kernel: [    0.000000]   DC000-DFFFF write-back
Jul  2 13:21:15 water kernel: [    0.000000]   E0000-FFFFF write-protect
Jul  2 13:21:15 water kernel: [    0.000000] MTRR variable ranges enabled:
Jul  2 13:21:15 water kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Jul  2 13:21:15 water kernel: [    0.000000]   1 base 040000000 mask FE0000000 write-back
Jul  2 13:21:15 water kernel: [    0.000000]   2 base 05FF80000 mask FFFF80000 uncachable
Jul  2 13:21:15 water kernel: [    0.000000]   3 disabled
Jul  2 13:21:15 water kernel: [    0.000000]   4 disabled
Jul  2 13:21:15 water kernel: [    0.000000]   5 disabled
Jul  2 13:21:15 water kernel: [    0.000000]   6 disabled
Jul  2 13:21:15 water kernel: [    0.000000]   7 disabled
Jul  2 13:21:15 water kernel: [    0.000000] PAT not supported by CPU.
Jul  2 13:21:15 water kernel: [    0.000000] original variable MTRRs
Jul  2 13:21:15 water kernel: [    0.000000] reg 0, base: 0GB, range: 1GB, type WB
Jul  2 13:21:15 water kernel: [    0.000000] reg 1, base: 1GB, range: 512MB, type WB
Jul  2 13:21:15 water kernel: [    0.000000] reg 2, base: 1572352KB, range: 512KB, type UC
Jul  2 13:21:15 water kernel: [    0.000000] total RAM covered: 1535M
Jul  2 13:21:15 water kernel: [    0.000000] Found optimal setting for mtrr clean up
Jul  2 13:21:15 water kernel: [    0.000000]  gran_size: 64K 	chunk_size: 1M 	num_reg: 3  	lose cover RAM: 0G
Jul  2 13:21:15 water kernel: [    0.000000] New variable MTRRs
Jul  2 13:21:15 water kernel: [    0.000000] reg 0, base: 0GB, range: 1GB, type WB
Jul  2 13:21:15 water kernel: [    0.000000] reg 1, base: 1GB, range: 512MB, type WB
Jul  2 13:21:15 water kernel: [    0.000000] reg 2, base: 1572352KB, range: 512KB, type UC
Jul  2 13:21:15 water kernel: [    0.000000] initial memory mapped : 0 - 01c00000
Jul  2 13:21:15 water kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Jul  2 13:21:15 water kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jul  2 13:21:15 water kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Jul  2 13:21:15 water kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Jul  2 13:21:15 water kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Jul  2 13:21:15 water kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
Jul  2 13:21:15 water kernel: [    0.000000] RAMDISK: 365fa000 - 372f5000
Jul  2 13:21:15 water kernel: [    0.000000] ACPI: RSDP 000f6d70 00024 (v02 IBM   )
Jul  2 13:21:15 water kernel: [    0.000000] ACPI: XSDT 5ff6a6cd 0004C (v01 IBM    TP-1R    00003180  LTP 00000000)
Jul  2 13:21:15 water kernel: [    0.000000] ACPI: FACP 5ff6a800 000F4 (v03 IBM    TP-1R    00003180 IBM  00000001)
Jul  2 13:21:15 water kernel: [    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 (20110413/tbfadt-529)
Jul  2 13:21:15 water kernel: [    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 0x000000000000102C/0x0 (20110413/tbfadt-560)
Jul  2 13:21:15 water kernel: [    0.000000] ACPI: DSDT 5ff6a9e7 0C4D5 (v01 IBM    TP-1R    00003180 MSFT 0100000E)
Jul  2 13:21:15 water kernel: [    0.000000] ACPI: FACS 5ff78000 00040
Jul  2 13:21:15 water kernel: [    0.000000] ACPI: SSDT 5ff6a9b4 00033 (v01 IBM    TP-1R    00003180 MSFT 0100000E)
Jul  2 13:21:15 water kernel: [    0.000000] ACPI: ECDT 5ff76ebc 00052 (v01 IBM    TP-1R    00003180 IBM  00000001)
Jul  2 13:21:15 water kernel: [    0.000000] ACPI: TCPA 5ff76f0e 00032 (v01 IBM    TP-1R    00003180 PTL  00000001)
Jul  2 13:21:15 water kernel: [    0.000000] ACPI: BOOT 5ff76fd8 00028 (v01 IBM    TP-1R    00003180  LTP 00000001)
Jul  2 13:21:15 water kernel: [    0.000000] 647MB HIGHMEM available.
Jul  2 13:21:15 water kernel: [    0.000000] 887MB LOWMEM available.
Jul  2 13:21:15 water kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jul  2 13:21:15 water kernel: [    0.000000]   low ram: 0 - 377fe000
Jul  2 13:21:15 water kernel: [    0.000000] Zone PFN ranges:
Jul  2 13:21:15 water kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jul  2 13:21:15 water kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jul  2 13:21:15 water kernel: [    0.000000]   HighMem  0x000377fe -> 0x0005ff60
Jul  2 13:21:15 water kernel: [    0.000000] Movable zone start PFN for each node
Jul  2 13:21:15 water kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul  2 13:21:15 water kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jul  2 13:21:15 water kernel: [    0.000000]     0: 0x00000100 -> 0x0005ff60
Jul  2 13:21:15 water kernel: [    0.000000] On node 0 totalpages: 392943
Jul  2 13:21:15 water kernel: [    0.000000] free_area_init_node: node 0, pgdat c17b11c0, node_mem_map f59fa200
Jul  2 13:21:15 water kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul  2 13:21:15 water kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul  2 13:21:15 water kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jul  2 13:21:15 water kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jul  2 13:21:15 water kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Jul  2 13:21:15 water kernel: [    0.000000]   HighMem zone: 1295 pages used for memmap
Jul  2 13:21:15 water kernel: [    0.000000]   HighMem zone: 164435 pages, LIFO batch:31
Jul  2 13:21:15 water kernel: [    0.000000] Using APIC driver default
Jul  2 13:21:15 water kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul  2 13:21:15 water kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jul  2 13:21:15 water kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Jul  2 13:21:15 water kernel: [    0.000000] APIC: disable apic facility
Jul  2 13:21:15 water kernel: [    0.000000] APIC: switched to apic NOOP
Jul  2 13:21:15 water kernel: [    0.000000] nr_irqs_gsi: 16
Jul  2 13:21:15 water kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul  2 13:21:15 water kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jul  2 13:21:15 water kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jul  2 13:21:15 water kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jul  2 13:21:15 water kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Jul  2 13:21:15 water kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 60000000:9f800000)
Jul  2 13:21:15 water kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul  2 13:21:15 water kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Jul  2 13:21:15 water kernel: [    0.000000] PERCPU: Embedded 12 pages/cpu @f5400000 s26240 r0 d22912 u4194304
Jul  2 13:21:15 water kernel: [    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
Jul  2 13:21:15 water kernel: [    0.000000] pcpu-alloc: [0] 0 
Jul  2 13:21:15 water kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 389872
Jul  2 13:21:15 water kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=6df79d67-e791-4ac7-a601-04b274f7b6fd ro quiet splash vt.handoff=7
Jul  2 13:21:15 water kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul  2 13:21:15 water kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul  2 13:21:15 water kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul  2 13:21:15 water kernel: [    0.000000] Initializing CPU#0
Jul  2 13:21:15 water kernel: [    0.000000] allocated 6288640 bytes of page_cgroup
Jul  2 13:21:15 water kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul  2 13:21:15 water kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0005ff60)
Jul  2 13:21:15 water kernel: [    0.000000] Memory: 1529628k/1572224k available (5329k kernel code, 42144k reserved, 2589k data, 696k init, 662920k highmem)
Jul  2 13:21:15 water kernel: [    0.000000] virtual kernel memory layout:
Jul  2 13:21:15 water kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Jul  2 13:21:15 water kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul  2 13:21:15 water kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jul  2 13:21:15 water kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jul  2 13:21:15 water kernel: [    0.000000]       .init : 0xc17bc000 - 0xc186a000   ( 696 kB)
Jul  2 13:21:15 water kernel: [    0.000000]       .data : 0xc1534784 - 0xc17bbd80   (2589 kB)
Jul  2 13:21:15 water kernel: [    0.000000]       .text : 0xc1000000 - 0xc1534784   (5329 kB)
Jul  2 13:21:15 water kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul  2 13:21:15 water kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Jul  2 13:21:15 water kernel: [    0.000000] Hierarchical RCU implementation.
Jul  2 13:21:15 water kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jul  2 13:21:15 water kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256 16
Jul  2 13:21:15 water kernel: [    0.000000] CPU 0 irqstacks, hard=f4806000 soft=f4808000
Jul  2 13:21:15 water kernel: [    0.000000] Extended CMOS year: 2000
Jul  2 13:21:15 water kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jul  2 13:21:15 water kernel: [    0.000000] Console: colour dummy device 80x25
Jul  2 13:21:15 water kernel: [    0.000000] console [tty0] enabled
Jul  2 13:21:15 water kernel: [    0.000000] Fast TSC calibration using PIT
Jul  2 13:21:15 water kernel: [    0.000000] Detected 1594.866 MHz processor.
Jul  2 13:21:15 water kernel: [    0.008006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3189.73 BogoMIPS (lpj=6379464)
Jul  2 13:21:15 water kernel: [    0.008013] pid_max: default: 32768 minimum: 301
Jul  2 13:21:15 water kernel: [    0.008051] Security Framework initialized
Jul  2 13:21:15 water kernel: [    0.008092] AppArmor: AppArmor initialized
Jul  2 13:21:15 water kernel: [    0.008095] Yama: becoming mindful.
Jul  2 13:21:15 water kernel: [    0.008194] Mount-cache hash table entries: 512
Jul  2 13:21:15 water kernel: [    0.008422] Initializing cgroup subsys cpuacct
Jul  2 13:21:15 water kernel: [    0.008432] Initializing cgroup subsys memory
Jul  2 13:21:15 water kernel: [    0.008446] Initializing cgroup subsys devices
Jul  2 13:21:15 water kernel: [    0.008450] Initializing cgroup subsys freezer
Jul  2 13:21:15 water kernel: [    0.008454] Initializing cgroup subsys net_cls
Jul  2 13:21:15 water kernel: [    0.008457] Initializing cgroup subsys blkio
Jul  2 13:21:15 water kernel: [    0.008469] Initializing cgroup subsys perf_event
Jul  2 13:21:15 water kernel: [    0.008523] mce: CPU supports 5 MCE banks
Jul  2 13:21:15 water kernel: [    0.008831] SMP alternatives: switching to UP code
Jul  2 13:21:15 water kernel: [    0.018420] Freeing SMP alternatives: 24k freed
Jul  2 13:21:15 water kernel: [    0.018434] ACPI: Core revision 20110413
Jul  2 13:21:15 water kernel: [    0.025735] ACPI: setting ELCR to 0200 (from 0800)
Jul  2 13:21:15 water kernel: [    0.028022] ftrace: allocating 24885 entries in 49 pages
Jul  2 13:21:15 water kernel: [    0.036139] weird, boot CPU (#0) not listed by the BIOS.
Jul  2 13:21:15 water kernel: [    0.036144] SMP motherboard not detected.
Jul  2 13:21:15 water kernel: [    0.036147] Local APIC not detected. Using dummy APIC emulation.
Jul  2 13:21:15 water kernel: [    0.036150] SMP disabled
Jul  2 13:21:15 water kernel: [    0.036153] Performance Events: 
Jul  2 13:21:15 water kernel: [    0.036157] no APIC, boot with the "lapic" boot parameter to force-enable it.
Jul  2 13:21:15 water kernel: [    0.036160] no hardware sampling interrupt available.
Jul  2 13:21:15 water kernel: [    0.036165] p6 PMU driver.
Jul  2 13:21:15 water kernel: [    0.036171] ... version:                0
Jul  2 13:21:15 water kernel: [    0.036173] ... bit width:              32
Jul  2 13:21:15 water kernel: [    0.036175] ... generic registers:      2
Jul  2 13:21:15 water kernel: [    0.036178] ... value mask:             00000000ffffffff
Jul  2 13:21:15 water kernel: [    0.036180] ... max period:             000000007fffffff
Jul  2 13:21:15 water kernel: [    0.036183] ... fixed-purpose events:   0
Jul  2 13:21:15 water kernel: [    0.036185] ... event mask:             0000000000000003
Jul  2 13:21:15 water kernel: [    0.036845] Brought up 1 CPUs
Jul  2 13:21:15 water kernel: [    0.036851] Total of 1 processors activated (3189.73 BogoMIPS).
Jul  2 13:21:15 water kernel: [    0.037063] devtmpfs: initialized
Jul  2 13:21:15 water kernel: [    0.037332] PM: Registering ACPI NVS region at 5ff77000 (8192 bytes)
Jul  2 13:21:15 water kernel: [    0.043711] print_constraints: dummy: 
Jul  2 13:21:15 water kernel: [    0.043738] Time: 17:20:55  Date: 07/02/12
Jul  2 13:21:15 water kernel: [    0.043804] NET: Registered protocol family 16
Jul  2 13:21:15 water kernel: [    0.044020] EISA bus registered
Jul  2 13:21:15 water kernel: [    0.044040] ACPI: bus type pci registered
Jul  2 13:21:15 water kernel: [    0.044447] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=8
Jul  2 13:21:15 water kernel: [    0.044451] PCI: Using configuration type 1 for base access
Jul  2 13:21:15 water kernel: [    0.045935] bio: create slab <bio-0> at 0
Jul  2 13:21:15 water kernel: [    0.048150] ACPI: EC: EC description table is found, configuring boot EC
Jul  2 13:21:15 water kernel: [    0.060388] ACPI: Interpreter enabled
Jul  2 13:21:15 water kernel: [    0.060395] ACPI: (supports S0 S3 S4 S5)
Jul  2 13:21:15 water kernel: [    0.060422] ACPI: Using PIC for interrupt routing
Jul  2 13:21:15 water kernel: [    0.064334] ACPI: Power Resource [PUBS] (on)
Jul  2 13:21:15 water kernel: [    0.068414] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Jul  2 13:21:15 water kernel: [    0.068954] ACPI: ACPI Dock Station Driver: 3 docks/bays found
Jul  2 13:21:15 water kernel: [    0.068954] HEST: Table not found.
Jul  2 13:21:15 water kernel: [    0.068954] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Jul  2 13:21:15 water kernel: [    0.068954] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul  2 13:21:15 water kernel: [    0.068954] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Jul  2 13:21:15 water kernel: [    0.068954] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Jul  2 13:21:15 water kernel: [    0.068954] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Jul  2 13:21:15 water kernel: [    0.068954] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
Jul  2 13:21:15 water kernel: [    0.068954] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
Jul  2 13:21:15 water kernel: [    0.068954] pci_root PNP0A03:00: host bridge window [mem 0x60000000-0xfebfffff] (ignored)
Jul  2 13:21:15 water kernel: [    0.068954] pci 0000:00:00.0: [8086:3340] type 0 class 0x000600
Jul  2 13:21:15 water kernel: [    0.068954] pci 0000:00:00.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
Jul  2 13:21:15 water kernel: [    0.068974] pci 0000:00:01.0: [8086:3341] type 1 class 0x000604
Jul  2 13:21:15 water kernel: [    0.069035] pci 0000:00:1d.0: [8086:24c2] type 0 class 0x000c03
Jul  2 13:21:15 water kernel: [    0.069081] pci 0000:00:1d.0: reg 20: [io  0x1800-0x181f]
Jul  2 13:21:15 water kernel: [    0.069117] pci 0000:00:1d.1: [8086:24c4] type 0 class 0x000c03
Jul  2 13:21:15 water kernel: [    0.069163] pci 0000:00:1d.1: reg 20: [io  0x1820-0x183f]
Jul  2 13:21:15 water kernel: [    0.069200] pci 0000:00:1d.2: [8086:24c7] type 0 class 0x000c03
Jul  2 13:21:15 water kernel: [    0.069246] pci 0000:00:1d.2: reg 20: [io  0x1840-0x185f]
Jul  2 13:21:15 water kernel: [    0.069293] pci 0000:00:1d.7: [8086:24cd] type 0 class 0x000c03
Jul  2 13:21:15 water kernel: [    0.069316] pci 0000:00:1d.7: reg 10: [mem 0xc0000000-0xc00003ff]
Jul  2 13:21:15 water kernel: [    0.069398] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jul  2 13:21:15 water kernel: [    0.069404] pci 0000:00:1d.7: PME# disabled
Jul  2 13:21:15 water kernel: [    0.069424] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
Jul  2 13:21:15 water kernel: [    0.069468] pci 0000:00:1f.0: [8086:24cc] type 0 class 0x000601
Jul  2 13:21:15 water kernel: [    0.069538] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH4 ACPI/GPIO/TCO
Jul  2 13:21:15 water kernel: [    0.069544] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH4 GPIO
Jul  2 13:21:15 water kernel: [    0.069561] pci 0000:00:1f.1: [8086:24ca] type 0 class 0x000101
Jul  2 13:21:15 water kernel: [    0.069576] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
Jul  2 13:21:15 water kernel: [    0.069588] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
Jul  2 13:21:15 water kernel: [    0.069599] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
Jul  2 13:21:15 water kernel: [    0.069610] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
Jul  2 13:21:15 water kernel: [    0.069621] pci 0000:00:1f.1: reg 20: [io  0x1860-0x186f]
Jul  2 13:21:15 water kernel: [    0.069633] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
Jul  2 13:21:15 water kernel: [    0.069663] pci 0000:00:1f.3: [8086:24c3] type 0 class 0x000c05
Jul  2 13:21:15 water kernel: [    0.069709] pci 0000:00:1f.3: reg 20: [io  0x1880-0x189f]
Jul  2 13:21:15 water kernel: [    0.069747] pci 0000:00:1f.5: [8086:24c5] type 0 class 0x000401
Jul  2 13:21:15 water kernel: [    0.069764] pci 0000:00:1f.5: reg 10: [io  0x1c00-0x1cff]
Jul  2 13:21:15 water kernel: [    0.069775] pci 0000:00:1f.5: reg 14: [io  0x18c0-0x18ff]
Jul  2 13:21:15 water kernel: [    0.069785] pci 0000:00:1f.5: reg 18: [mem 0xc0000c00-0xc0000dff]
Jul  2 13:21:15 water kernel: [    0.069796] pci 0000:00:1f.5: reg 1c: [mem 0xc0000800-0xc00008ff]
Jul  2 13:21:15 water kernel: [    0.069836] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Jul  2 13:21:15 water kernel: [    0.069841] pci 0000:00:1f.5: PME# disabled
Jul  2 13:21:15 water kernel: [    0.069859] pci 0000:00:1f.6: [8086:24c6] type 0 class 0x000703
Jul  2 13:21:15 water kernel: [    0.069875] pci 0000:00:1f.6: reg 10: [io  0x2400-0x24ff]
Jul  2 13:21:15 water kernel: [    0.069886] pci 0000:00:1f.6: reg 14: [io  0x2000-0x207f]
Jul  2 13:21:15 water kernel: [    0.069939] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
Jul  2 13:21:15 water kernel: [    0.069945] pci 0000:00:1f.6: PME# disabled
Jul  2 13:21:15 water kernel: [    0.069973] pci 0000:01:00.0: [1002:4c66] type 0 class 0x000300
Jul  2 13:21:15 water kernel: [    0.069990] pci 0000:01:00.0: reg 10: [mem 0xe0000000-0xe7ffffff pref]
Jul  2 13:21:15 water kernel: [    0.069999] pci 0000:01:00.0: reg 14: [io  0x3000-0x30ff]
Jul  2 13:21:15 water kernel: [    0.070008] pci 0000:01:00.0: reg 18: [mem 0xc0100000-0xc010ffff]
Jul  2 13:21:15 water kernel: [    0.070033] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Jul  2 13:21:15 water kernel: [    0.070054] pci 0000:01:00.0: supports D1 D2
Jul  2 13:21:15 water kernel: [    0.070090] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jul  2 13:21:15 water kernel: [    0.070095] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
Jul  2 13:21:15 water kernel: [    0.070100] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
Jul  2 13:21:15 water kernel: [    0.070105] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe7ffffff pref]
Jul  2 13:21:15 water kernel: [    0.070131] pci 0000:02:00.0: [104c:ac55] type 2 class 0x000607
Jul  2 13:21:15 water kernel: [    0.070150] pci 0000:02:00.0: reg 10: [mem 0xb0000000-0xb0000fff]
Jul  2 13:21:15 water kernel: [    0.070170] pci 0000:02:00.0: supports D1 D2
Jul  2 13:21:15 water kernel: [    0.070173] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  2 13:21:15 water kernel: [    0.070179] pci 0000:02:00.0: PME# disabled
Jul  2 13:21:15 water kernel: [    0.070198] pci 0000:02:00.1: [104c:ac55] type 2 class 0x000607
Jul  2 13:21:15 water kernel: [    0.070217] pci 0000:02:00.1: reg 10: [mem 0xb1000000-0xb1000fff]
Jul  2 13:21:15 water kernel: [    0.070237] pci 0000:02:00.1: supports D1 D2
Jul  2 13:21:15 water kernel: [    0.070240] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot D3cold
Jul  2 13:21:15 water kernel: [    0.070246] pci 0000:02:00.1: PME# disabled
Jul  2 13:21:15 water kernel: [    0.070274] pci 0000:02:01.0: [8086:101e] type 0 class 0x000200
Jul  2 13:21:15 water kernel: [    0.070294] pci 0000:02:01.0: reg 10: [mem 0xc0220000-0xc023ffff]
Jul  2 13:21:15 water kernel: [    0.070305] pci 0000:02:01.0: reg 14: [mem 0xc0200000-0xc020ffff]
Jul  2 13:21:15 water kernel: [    0.070317] pci 0000:02:01.0: reg 18: [io  0x8000-0x803f]
Jul  2 13:21:15 water kernel: [    0.070350] pci 0000:02:01.0: reg 30: [mem 0x00000000-0x0000ffff pref]
Jul  2 13:21:15 water kernel: [    0.070375] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
Jul  2 13:21:15 water kernel: [    0.070380] pci 0000:02:01.0: PME# disabled
Jul  2 13:21:15 water kernel: [    0.070401] pci 0000:02:02.0: [168c:0012] type 0 class 0x000200
Jul  2 13:21:15 water kernel: [    0.070419] pci 0000:02:02.0: reg 10: [mem 0xc0210000-0xc021ffff]
Jul  2 13:21:15 water kernel: [    0.070522] pci 0000:00:1e.0: PCI bridge to [bus 02-08] (subtractive decode)
Jul  2 13:21:15 water kernel: [    0.070528] pci 0000:00:1e.0:   bridge window [io  0x4000-0x8fff]
Jul  2 13:21:15 water kernel: [    0.070534] pci 0000:00:1e.0:   bridge window [mem 0xc0200000-0xcfffffff]
Jul  2 13:21:15 water kernel: [    0.070540] pci 0000:00:1e.0:   bridge window [mem 0xe8000000-0xefffffff pref]
Jul  2 13:21:15 water kernel: [    0.070544] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Jul  2 13:21:15 water kernel: [    0.070548] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
Jul  2 13:21:15 water kernel: [    0.070629] pci_bus 0000:00: on NUMA node 0
Jul  2 13:21:15 water kernel: [    0.070633] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul  2 13:21:15 water kernel: [    0.070688] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Jul  2 13:21:15 water kernel: [    0.070717] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Jul  2 13:21:15 water kernel: [    0.072021]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
Jul  2 13:21:15 water kernel: [    0.075292] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:21:15 water kernel: [    0.075399] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:21:15 water kernel: [    0.075504] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:21:15 water kernel: [    0.075607] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:21:15 water kernel: [    0.075690] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Jul  2 13:21:15 water kernel: [    0.075774] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Jul  2 13:21:15 water kernel: [    0.075858] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Jul  2 13:21:15 water kernel: [    0.075963] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:21:15 water kernel: [    0.076123] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jul  2 13:21:15 water kernel: [    0.076129] vgaarb: loaded
Jul  2 13:21:15 water kernel: [    0.076131] vgaarb: bridge control possible 0000:01:00.0
Jul  2 13:21:15 water kernel: [    0.076474] SCSI subsystem initialized
Jul  2 13:21:15 water kernel: [    0.076564] libata version 3.00 loaded.
Jul  2 13:21:15 water kernel: [    0.076636] usbcore: registered new interface driver usbfs
Jul  2 13:21:15 water kernel: [    0.076654] usbcore: registered new interface driver hub
Jul  2 13:21:15 water kernel: [    0.076690] usbcore: registered new device driver usb
Jul  2 13:21:15 water kernel: [    0.076813] PCI: Using ACPI for IRQ routing
Jul  2 13:21:15 water kernel: [    0.076953] PCI: pci_cache_line_size set to 64 bytes
Jul  2 13:21:15 water kernel: [    0.077022] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
Jul  2 13:21:15 water kernel: [    0.077026] reserve RAM buffer: 000000005ff60000 - 000000005fffffff 
Jul  2 13:21:15 water kernel: [    0.077184] NetLabel: Initializing
Jul  2 13:21:15 water kernel: [    0.077187] NetLabel:  domain hash size = 128
Jul  2 13:21:15 water kernel: [    0.077189] NetLabel:  protocols = UNLABELED CIPSOv4
Jul  2 13:21:15 water kernel: [    0.077207] NetLabel:  unlabeled traffic allowed by default
Jul  2 13:21:15 water kernel: [    0.077276] Switching to clocksource pit
Jul  2 13:21:15 water kernel: [    0.087703] AppArmor: AppArmor Filesystem Enabled
Jul  2 13:21:15 water kernel: [    0.087771] pnp: PnP ACPI init
Jul  2 13:21:15 water kernel: [    0.087804] ACPI: bus type pnp registered
Jul  2 13:21:15 water kernel: [    0.088497] pnp 00:00: [mem 0x00000000-0x0009ffff]
Jul  2 13:21:15 water kernel: [    0.088502] pnp 00:00: [mem 0x000c0000-0x000c3fff]
Jul  2 13:21:15 water kernel: [    0.088505] pnp 00:00: [mem 0x000c4000-0x000c7fff]
Jul  2 13:21:15 water kernel: [    0.088508] pnp 00:00: [mem 0x000c8000-0x000cbfff]
Jul  2 13:21:15 water kernel: [    0.088512] pnp 00:00: [mem 0x000cc000-0x000cffff]
Jul  2 13:21:15 water kernel: [    0.088515] pnp 00:00: [mem 0x000d0000-0x000d3fff]
Jul  2 13:21:15 water kernel: [    0.088519] pnp 00:00: [mem 0x000d4000-0x000d3fff disabled]
Jul  2 13:21:15 water kernel: [    0.088522] pnp 00:00: [mem 0x000d8000-0x000d7fff disabled]
Jul  2 13:21:15 water kernel: [    0.088526] pnp 00:00: [mem 0x000dc000-0x000dffff]
Jul  2 13:21:15 water kernel: [    0.088529] pnp 00:00: [mem 0x000e0000-0x000e3fff]
Jul  2 13:21:15 water kernel: [    0.088532] pnp 00:00: [mem 0x000e4000-0x000e7fff]
Jul  2 13:21:15 water kernel: [    0.088536] pnp 00:00: [mem 0x000e8000-0x000ebfff]
Jul  2 13:21:15 water kernel: [    0.088539] pnp 00:00: [mem 0x000ec000-0x000effff]
Jul  2 13:21:15 water kernel: [    0.088542] pnp 00:00: [mem 0x000f0000-0x000fffff]
Jul  2 13:21:15 water kernel: [    0.088556] pnp 00:00: [mem 0x00100000-0x5fffffff]
Jul  2 13:21:15 water kernel: [    0.088559] pnp 00:00: [mem 0xfec00000-0xffffffff]
Jul  2 13:21:15 water kernel: [    0.088683] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
Jul  2 13:21:15 water kernel: [    0.088689] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
Jul  2 13:21:15 water kernel: [    0.088693] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
Jul  2 13:21:15 water kernel: [    0.088697] system 00:00: [mem 0x000c8000-0x000cbfff] could not be reserved
Jul  2 13:21:15 water kernel: [    0.088702] system 00:00: [mem 0x000cc000-0x000cffff] could not be reserved
Jul  2 13:21:15 water kernel: [    0.088706] system 00:00: [mem 0x000d0000-0x000d3fff] could not be reserved
Jul  2 13:21:15 water kernel: [    0.088710] system 00:00: [mem 0x000dc000-0x000dffff] could not be reserved
Jul  2 13:21:15 water kernel: [    0.088715] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
Jul  2 13:21:15 water kernel: [    0.088719] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
Jul  2 13:21:15 water kernel: [    0.088723] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
Jul  2 13:21:15 water kernel: [    0.088727] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
Jul  2 13:21:15 water kernel: [    0.088732] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
Jul  2 13:21:15 water kernel: [    0.088736] system 00:00: [mem 0x00100000-0x5fffffff] could not be reserved
Jul  2 13:21:15 water kernel: [    0.088741] system 00:00: [mem 0xfec00000-0xffffffff] could not be reserved
Jul  2 13:21:15 water kernel: [    0.088747] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Jul  2 13:21:15 water kernel: [    0.088787] pnp 00:01: [bus 00-ff]
Jul  2 13:21:15 water kernel: [    0.088791] pnp 00:01: [io  0x0cf8-0x0cff]
Jul  2 13:21:15 water kernel: [    0.088795] pnp 00:01: [io  0x0000-0x0cf7 window]
Jul  2 13:21:15 water kernel: [    0.088799] pnp 00:01: [io  0x0d00-0xffff window]
Jul  2 13:21:15 water kernel: [    0.088802] pnp 00:01: [mem 0x000a0000-0x000bffff window]
Jul  2 13:21:15 water kernel: [    0.088806] pnp 00:01: [mem 0x000c0000-0x000c3fff window]
Jul  2 13:21:15 water kernel: [    0.088810] pnp 00:01: [mem 0x000c4000-0x000c7fff window]
Jul  2 13:21:15 water kernel: [    0.088813] pnp 00:01: [mem 0x000c8000-0x000cbfff window]
Jul  2 13:21:15 water kernel: [    0.088817] pnp 00:01: [mem 0x000cc000-0x000cffff window]
Jul  2 13:21:15 water kernel: [    0.088820] pnp 00:01: [mem 0x000d0000-0x000d3fff window]
Jul  2 13:21:15 water kernel: [    0.088824] pnp 00:01: [mem 0x000d4000-0x000d7fff window]
Jul  2 13:21:15 water kernel: [    0.088827] pnp 00:01: [mem 0x000d8000-0x000dbfff window]
Jul  2 13:21:15 water kernel: [    0.088831] pnp 00:01: [mem 0x000dc000-0x000dffff window]
Jul  2 13:21:15 water kernel: [    0.088834] pnp 00:01: [mem 0x000e0000-0x000e3fff window]
Jul  2 13:21:15 water kernel: [    0.088838] pnp 00:01: [mem 0x000e4000-0x000e7fff window]
Jul  2 13:21:15 water kernel: [    0.088842] pnp 00:01: [mem 0x000e8000-0x000ebfff window]
Jul  2 13:21:15 water kernel: [    0.088845] pnp 00:01: [mem 0x000ec000-0x000effff window]
Jul  2 13:21:15 water kernel: [    0.088849] pnp 00:01: [mem 0x60000000-0xfebfffff window]
Jul  2 13:21:15 water kernel: [    0.088927] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
Jul  2 13:21:15 water kernel: [    0.089051] pnp 00:02: [io  0x0010-0x001f]
Jul  2 13:21:15 water kernel: [    0.089054] pnp 00:02: [io  0x0090-0x009f]
Jul  2 13:21:15 water kernel: [    0.089058] pnp 00:02: [io  0x0024-0x0025]
Jul  2 13:21:15 water kernel: [    0.089061] pnp 00:02: [io  0x0028-0x0029]
Jul  2 13:21:15 water kernel: [    0.089064] pnp 00:02: [io  0x002c-0x002d]
Jul  2 13:21:15 water kernel: [    0.089067] pnp 00:02: [io  0x0030-0x0031]
Jul  2 13:21:15 water kernel: [    0.089070] pnp 00:02: [io  0x0034-0x0035]
Jul  2 13:21:15 water kernel: [    0.089073] pnp 00:02: [io  0x0038-0x0039]
Jul  2 13:21:15 water kernel: [    0.089076] pnp 00:02: [io  0x003c-0x003d]
Jul  2 13:21:15 water kernel: [    0.089079] pnp 00:02: [io  0x00a4-0x00a5]
Jul  2 13:21:15 water kernel: [    0.089082] pnp 00:02: [io  0x00a8-0x00a9]
Jul  2 13:21:15 water kernel: [    0.089085] pnp 00:02: [io  0x00ac-0x00ad]
Jul  2 13:21:15 water kernel: [    0.089088] pnp 00:02: [io  0x00b0-0x00b5]
Jul  2 13:21:15 water kernel: [    0.089091] pnp 00:02: [io  0x00b8-0x00b9]
Jul  2 13:21:15 water kernel: [    0.089094] pnp 00:02: [io  0x00bc-0x00bd]
Jul  2 13:21:15 water kernel: [    0.089097] pnp 00:02: [io  0x0050-0x0053]
Jul  2 13:21:15 water kernel: [    0.089100] pnp 00:02: [io  0x0072-0x0077]
Jul  2 13:21:15 water kernel: [    0.089103] pnp 00:02: [io  0x002e-0x002f]
Jul  2 13:21:15 water kernel: [    0.089107] pnp 00:02: [io  0x1000-0x107f]
Jul  2 13:21:15 water kernel: [    0.089110] pnp 00:02: [io  0x1180-0x11bf]
Jul  2 13:21:15 water kernel: [    0.089113] pnp 00:02: [io  0x15e0-0x15ef]
Jul  2 13:21:15 water kernel: [    0.089116] pnp 00:02: [io  0x1600-0x162f]
Jul  2 13:21:15 water kernel: [    0.089119] pnp 00:02: [io  0x1632-0x167f]
Jul  2 13:21:15 water kernel: [    0.089122] pnp 00:02: [io  0x004e-0x004f]
Jul  2 13:21:15 water kernel: [    0.089125] pnp 00:02: [io  0x1630-0x1631]
Jul  2 13:21:15 water kernel: [    0.089215] system 00:02: [io  0x1000-0x107f] has been reserved
Jul  2 13:21:15 water kernel: [    0.089220] system 00:02: [io  0x1180-0x11bf] has been reserved
Jul  2 13:21:15 water kernel: [    0.089224] system 00:02: [io  0x15e0-0x15ef] has been reserved
Jul  2 13:21:15 water kernel: [    0.089228] system 00:02: [io  0x1600-0x162f] has been reserved
Jul  2 13:21:15 water kernel: [    0.089232] system 00:02: [io  0x1632-0x167f] has been reserved
Jul  2 13:21:15 water kernel: [    0.089236] system 00:02: [io  0x1630-0x1631] has been reserved
Jul  2 13:21:15 water kernel: [    0.089241] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul  2 13:21:15 water kernel: [    0.089261] pnp 00:03: [io  0x0000-0x000f]
Jul  2 13:21:15 water kernel: [    0.089264] pnp 00:03: [io  0x0080-0x008f]
Jul  2 13:21:15 water kernel: [    0.089268] pnp 00:03: [io  0x00c0-0x00df]
Jul  2 13:21:15 water kernel: [    0.089272] pnp 00:03: [dma 4]
Jul  2 13:21:15 water kernel: [    0.089309] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Jul  2 13:21:15 water kernel: [    0.089322] pnp 00:04: [io  0x0061]
Jul  2 13:21:15 water kernel: [    0.089358] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Jul  2 13:21:15 water kernel: [    0.089371] pnp 00:05: [io  0x00f0]
Jul  2 13:21:15 water kernel: [    0.089378] pnp 00:05: [irq 13]
Jul  2 13:21:15 water kernel: [    0.089421] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Jul  2 13:21:15 water kernel: [    0.089435] pnp 00:06: [io  0x0070-0x0071]
Jul  2 13:21:15 water kernel: [    0.089438] pnp 00:06: [irq 8]
Jul  2 13:21:15 water kernel: [    0.089475] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul  2 13:21:15 water kernel: [    0.089489] pnp 00:07: [io  0x0060]
Jul  2 13:21:15 water kernel: [    0.089492] pnp 00:07: [io  0x0064]
Jul  2 13:21:15 water kernel: [    0.089495] pnp 00:07: [irq 1]
Jul  2 13:21:15 water kernel: [    0.089532] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
Jul  2 13:21:15 water kernel: [    0.089545] pnp 00:08: [irq 12]
Jul  2 13:21:15 water kernel: [    0.089584] pnp 00:08: Plug and Play ACPI device, IDs IBM0057 PNP0f13 (active)
Jul  2 13:21:15 water kernel: [    0.089631] pnp 00:09: [io  0x03f0-0x03f5]
Jul  2 13:21:15 water kernel: [    0.089635] pnp 00:09: [io  0x03f7]
Jul  2 13:21:15 water kernel: [    0.089638] pnp 00:09: [irq 6]
Jul  2 13:21:15 water kernel: [    0.089641] pnp 00:09: [dma 2]
Jul  2 13:21:15 water kernel: [    0.089704] pnp 00:09: Plug and Play ACPI device, IDs PNP0700 (active)
Jul  2 13:21:15 water kernel: [    0.089833] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (disabled)
Jul  2 13:21:15 water kernel: [    0.089958] pnp 00:0b: [io  0x03bc-0x03be]
Jul  2 13:21:15 water kernel: [    0.089962] pnp 00:0b: [irq 7]
Jul  2 13:21:15 water kernel: [    0.090055] pnp 00:0b: Plug and Play ACPI device, IDs PNP0400 (active)
Jul  2 13:21:15 water kernel: [    0.090214] pnp 00:0c: Plug and Play ACPI device, IDs IBM0071 PNP0511 (disabled)
Jul  2 13:21:15 water kernel: [    0.090938] pnp: PnP ACPI: found 13 devices
Jul  2 13:21:15 water kernel: [    0.090941] ACPI: ACPI bus type pnp unregistered
Jul  2 13:21:15 water kernel: [    0.090947] PnPBIOS: Disabled by ACPI PNP
Jul  2 13:21:15 water kernel: [    0.127883] Switching to clocksource acpi_pm
Jul  2 13:21:15 water kernel: [    0.127922] PCI: max bus depth: 2 pci_try_num: 3
Jul  2 13:21:15 water kernel: [    0.127955] pci 0000:00:1f.1: BAR 5: assigned [mem 0x60000000-0x600003ff]
Jul  2 13:21:15 water kernel: [    0.127964] pci 0000:00:1f.1: BAR 5: set to [mem 0x60000000-0x600003ff] (PCI address [0x60000000-0x600003ff])
Jul  2 13:21:15 water kernel: [    0.127971] pci 0000:01:00.0: BAR 6: assigned [mem 0xc0120000-0xc013ffff pref]
Jul  2 13:21:15 water kernel: [    0.127976] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jul  2 13:21:15 water kernel: [    0.127980] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
Jul  2 13:21:15 water kernel: [    0.127986] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
Jul  2 13:21:15 water kernel: [    0.127991] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe7ffffff pref]
Jul  2 13:21:15 water kernel: [    0.128000] pci 0000:02:00.0: BAR 15: assigned [mem 0xe8000000-0xebffffff pref]
Jul  2 13:21:15 water kernel: [    0.128005] pci 0000:02:00.0: BAR 16: assigned [mem 0xc4000000-0xc7ffffff]
Jul  2 13:21:15 water kernel: [    0.128009] pci 0000:02:00.1: BAR 15: assigned [mem 0xec000000-0xefffffff pref]
Jul  2 13:21:15 water kernel: [    0.128014] pci 0000:02:00.1: BAR 16: assigned [mem 0xc8000000-0xcbffffff]
Jul  2 13:21:15 water kernel: [    0.128019] pci 0000:02:01.0: BAR 6: assigned [mem 0xc0240000-0xc024ffff pref]
Jul  2 13:21:15 water kernel: [    0.128023] pci 0000:02:00.0: BAR 13: assigned [io  0x4000-0x40ff]
Jul  2 13:21:15 water kernel: [    0.128027] pci 0000:02:00.0: BAR 14: assigned [io  0x4400-0x44ff]
Jul  2 13:21:15 water kernel: [    0.128031] pci 0000:02:00.1: BAR 13: assigned [io  0x4800-0x48ff]
Jul  2 13:21:15 water kernel: [    0.128034] pci 0000:02:00.1: BAR 14: assigned [io  0x4c00-0x4cff]
Jul  2 13:21:15 water kernel: [    0.128039] pci 0000:02:00.0: CardBus bridge to [bus 03-06]
Jul  2 13:21:15 water kernel: [    0.128042] pci 0000:02:00.0:   bridge window [io  0x4000-0x40ff]
Jul  2 13:21:15 water kernel: [    0.128048] pci 0000:02:00.0:   bridge window [io  0x4400-0x44ff]
Jul  2 13:21:15 water kernel: [    0.128054] pci 0000:02:00.0:   bridge window [mem 0xe8000000-0xebffffff pref]
Jul  2 13:21:15 water kernel: [    0.128060] pci 0000:02:00.0:   bridge window [mem 0xc4000000-0xc7ffffff]
Jul  2 13:21:15 water kernel: [    0.128065] pci 0000:02:00.1: CardBus bridge to [bus 07-07]
Jul  2 13:21:15 water kernel: [    0.128069] pci 0000:02:00.1:   bridge window [io  0x4800-0x48ff]
Jul  2 13:21:15 water kernel: [    0.128074] pci 0000:02:00.1:   bridge window [io  0x4c00-0x4cff]
Jul  2 13:21:15 water kernel: [    0.128080] pci 0000:02:00.1:   bridge window [mem 0xec000000-0xefffffff pref]
Jul  2 13:21:15 water kernel: [    0.128086] pci 0000:02:00.1:   bridge window [mem 0xc8000000-0xcbffffff]
Jul  2 13:21:15 water kernel: [    0.128092] pci 0000:00:1e.0: PCI bridge to [bus 02-08]
Jul  2 13:21:15 water kernel: [    0.128096] pci 0000:00:1e.0:   bridge window [io  0x4000-0x8fff]
Jul  2 13:21:15 water kernel: [    0.128103] pci 0000:00:1e.0:   bridge window [mem 0xc0200000-0xcfffffff]
Jul  2 13:21:15 water kernel: [    0.128109] pci 0000:00:1e.0:   bridge window [mem 0xe8000000-0xefffffff pref]
Jul  2 13:21:15 water kernel: [    0.128132] pci 0000:00:1e.0: setting latency timer to 64
Jul  2 13:21:15 water kernel: [    0.128367] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Jul  2 13:21:15 water kernel: [    0.128372] PCI: setting IRQ 11 as level-triggered
Jul  2 13:21:15 water kernel: [    0.128379] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:21:15 water kernel: [    0.128563] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Jul  2 13:21:15 water kernel: [    0.128568] pci 0000:02:00.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:21:15 water kernel: [    0.128577] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Jul  2 13:21:15 water kernel: [    0.128580] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
Jul  2 13:21:15 water kernel: [    0.128584] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
Jul  2 13:21:15 water kernel: [    0.128588] pci_bus 0000:01: resource 1 [mem 0xc0100000-0xc01fffff]
Jul  2 13:21:15 water kernel: [    0.128592] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xe7ffffff pref]
Jul  2 13:21:15 water kernel: [    0.128596] pci_bus 0000:02: resource 0 [io  0x4000-0x8fff]
Jul  2 13:21:15 water kernel: [    0.128600] pci_bus 0000:02: resource 1 [mem 0xc0200000-0xcfffffff]
Jul  2 13:21:15 water kernel: [    0.128604] pci_bus 0000:02: resource 2 [mem 0xe8000000-0xefffffff pref]
Jul  2 13:21:15 water kernel: [    0.128608] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
Jul  2 13:21:15 water kernel: [    0.128611] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
Jul  2 13:21:15 water kernel: [    0.128615] pci_bus 0000:03: resource 0 [io  0x4000-0x40ff]
Jul  2 13:21:15 water kernel: [    0.128619] pci_bus 0000:03: resource 1 [io  0x4400-0x44ff]
Jul  2 13:21:15 water kernel: [    0.128623] pci_bus 0000:03: resource 2 [mem 0xe8000000-0xebffffff pref]
Jul  2 13:21:15 water kernel: [    0.128627] pci_bus 0000:03: resource 3 [mem 0xc4000000-0xc7ffffff]
Jul  2 13:21:15 water kernel: [    0.128630] pci_bus 0000:07: resource 0 [io  0x4800-0x48ff]
Jul  2 13:21:15 water kernel: [    0.128634] pci_bus 0000:07: resource 1 [io  0x4c00-0x4cff]
Jul  2 13:21:15 water kernel: [    0.128638] pci_bus 0000:07: resource 2 [mem 0xec000000-0xefffffff pref]
Jul  2 13:21:15 water kernel: [    0.128642] pci_bus 0000:07: resource 3 [mem 0xc8000000-0xcbffffff]
Jul  2 13:21:15 water kernel: [    0.128721] NET: Registered protocol family 2
Jul  2 13:21:15 water kernel: [    0.128824] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul  2 13:21:15 water kernel: [    0.129233] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul  2 13:21:15 water kernel: [    0.130786] Switched to NOHz mode on CPU #0
Jul  2 13:21:15 water kernel: [    0.131176] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul  2 13:21:15 water kernel: [    0.132341] TCP: Hash tables configured (established 131072 bind 65536)
Jul  2 13:21:15 water kernel: [    0.132347] TCP reno registered
Jul  2 13:21:15 water kernel: [    0.132358] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jul  2 13:21:15 water kernel: [    0.132397] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jul  2 13:21:15 water kernel: [    0.132644] NET: Registered protocol family 1
Jul  2 13:21:15 water kernel: [    0.132776] pci 0000:01:00.0: Boot video device
Jul  2 13:21:15 water kernel: [    0.132794] PCI: CLS 32 bytes, default 64
Jul  2 13:21:15 water kernel: [    0.132922] Simple Boot Flag at 0x35 set to 0x1
Jul  2 13:21:15 water kernel: [    0.133379] audit: initializing netlink socket (disabled)
Jul  2 13:21:15 water kernel: [    0.133402] type=2000 audit(1341249655.127:1): initialized
Jul  2 13:21:15 water kernel: [    0.163763] Trying to unpack rootfs image as initramfs...
Jul  2 13:21:15 water kernel: [    0.212518] highmem bounce pool size: 64 pages
Jul  2 13:21:15 water kernel: [    0.212529] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul  2 13:21:15 water kernel: [    0.244678] VFS: Disk quotas dquot_6.5.2
Jul  2 13:21:15 water kernel: [    0.244806] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul  2 13:21:15 water kernel: [    0.246045] fuse init (API version 7.16)
Jul  2 13:21:15 water kernel: [    0.246197] msgmni has been set to 1692
Jul  2 13:21:15 water kernel: [    0.260624] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul  2 13:21:15 water kernel: [    0.260669] io scheduler noop registered
Jul  2 13:21:15 water kernel: [    0.260672] io scheduler deadline registered
Jul  2 13:21:15 water kernel: [    0.260701] io scheduler cfq registered (default)
Jul  2 13:21:15 water kernel: [    0.260930] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  2 13:21:15 water kernel: [    0.260966] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul  2 13:21:15 water kernel: [    0.261249] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jul  2 13:21:15 water kernel: [    0.261415] ACPI: AC Adapter [AC] (on-line)
Jul  2 13:21:15 water kernel: [    0.261520] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Jul  2 13:21:15 water kernel: [    0.261718] ACPI: Lid Switch [LID]
Jul  2 13:21:15 water kernel: [    0.261781] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Jul  2 13:21:15 water kernel: [    0.261789] ACPI: Sleep Button [SLPB]
Jul  2 13:21:15 water kernel: [    0.261861] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jul  2 13:21:15 water kernel: [    0.261866] ACPI: Power Button [PWRF]
Jul  2 13:21:15 water kernel: [    0.261897] ACPI: acpi_idle registered with cpuidle
Jul  2 13:21:15 water kernel: [    0.262359] Marking TSC unstable due to TSC halts in idle
Jul  2 13:21:15 water kernel: [    0.270627] thermal LNXTHERM:00: registered as thermal_zone0
Jul  2 13:21:15 water kernel: [    0.270632] ACPI: Thermal Zone [THM0] (69 C)
Jul  2 13:21:15 water kernel: [    0.270671] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jul  2 13:21:15 water kernel: [    0.270701] ERST: Table is not found!
Jul  2 13:21:15 water kernel: [    0.270849] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul  2 13:21:15 water kernel: [    0.272686] serial 00:0a: [io  0x03f8-0x03ff]
Jul  2 13:21:15 water kernel: [    0.272746] serial 00:0a: [irq 4]
Jul  2 13:21:15 water kernel: [    0.273094] serial 00:0a: activated
Jul  2 13:21:15 water kernel: [    0.273226] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
Jul  2 13:21:15 water kernel: [    0.273369] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:21:15 water kernel: [    0.273379] serial 0000:00:1f.6: PCI INT B disabled
Jul  2 13:21:15 water kernel: [    0.273545] Linux agpgart interface v0.103
Jul  2 13:21:15 water kernel: [    0.273673] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
Jul  2 13:21:15 water kernel: [    0.292621] isapnp: Scanning for PnP cards...
Jul  2 13:21:15 water kernel: [    0.357700] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Jul  2 13:21:15 water kernel: [    0.359610] brd: module loaded
Jul  2 13:21:15 water kernel: [    0.451882] loop: module loaded
Jul  2 13:21:15 water kernel: [    0.452196] ata_piix 0000:00:1f.1: version 2.13
Jul  2 13:21:15 water kernel: [    0.452213] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
Jul  2 13:21:15 water kernel: [    0.452476] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Jul  2 13:21:15 water kernel: [    0.452484] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:21:15 water kernel: [    0.452546] ata_piix 0000:00:1f.1: setting latency timer to 64
Jul  2 13:21:15 water kernel: [    0.456418] scsi0 : ata_piix
Jul  2 13:21:15 water kernel: [    0.456634] scsi1 : ata_piix
Jul  2 13:21:15 water kernel: [    0.457319] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
Jul  2 13:21:15 water kernel: [    0.457324] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
Jul  2 13:21:15 water kernel: [    0.457931] Fixed MDIO Bus: probed
Jul  2 13:21:15 water kernel: [    0.457971] PPP generic driver version 2.4.2
Jul  2 13:21:15 water kernel: [    0.458089] tun: Universal TUN/TAP device driver, 1.6
Jul  2 13:21:15 water kernel: [    0.458092] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul  2 13:21:15 water kernel: [    0.458247] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul  2 13:21:15 water kernel: [    0.458272] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Jul  2 13:21:15 water kernel: [    0.458278] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Jul  2 13:21:15 water kernel: [    0.458490] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Jul  2 13:21:15 water kernel: [    0.458497] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:21:15 water kernel: [    0.458522] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jul  2 13:21:15 water kernel: [    0.458527] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul  2 13:21:15 water kernel: [    0.458577] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jul  2 13:21:15 water kernel: [    0.458620] ehci_hcd 0000:00:1d.7: debug port 1
Jul  2 13:21:15 water kernel: [    0.462512] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Jul  2 13:21:15 water kernel: [    0.468274] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
Jul  2 13:21:15 water kernel: [    0.488083] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jul  2 13:21:15 water kernel: [    0.488400] hub 1-0:1.0: USB hub found
Jul  2 13:21:15 water kernel: [    0.488409] hub 1-0:1.0: 6 ports detected
Jul  2 13:21:15 water kernel: [    0.488532] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul  2 13:21:15 water kernel: [    0.488560] uhci_hcd: USB Universal Host Controller Interface driver
Jul  2 13:21:15 water kernel: [    0.488658] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Jul  2 13:21:15 water kernel: [    0.488663] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Jul  2 13:21:15 water kernel: [    0.488678] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:21:15 water kernel: [    0.488692] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jul  2 13:21:15 water kernel: [    0.488697] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul  2 13:21:15 water kernel: [    0.488770] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jul  2 13:21:15 water kernel: [    0.488806] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
Jul  2 13:21:15 water kernel: [    0.488997] hub 2-0:1.0: USB hub found
Jul  2 13:21:15 water kernel: [    0.489003] hub 2-0:1.0: 2 ports detected
Jul  2 13:21:15 water kernel: [    0.489078] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Jul  2 13:21:15 water kernel: [    0.489082] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Jul  2 13:21:15 water kernel: [    0.489348] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Jul  2 13:21:15 water kernel: [    0.489354] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:21:15 water kernel: [    0.489362] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jul  2 13:21:15 water kernel: [    0.489367] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul  2 13:21:15 water kernel: [    0.489430] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jul  2 13:21:15 water kernel: [    0.489455] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
Jul  2 13:21:15 water kernel: [    0.489646] hub 3-0:1.0: USB hub found
Jul  2 13:21:15 water kernel: [    0.489652] hub 3-0:1.0: 2 ports detected
Jul  2 13:21:15 water kernel: [    0.489726] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:21:15 water kernel: [    0.489734] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jul  2 13:21:15 water kernel: [    0.489738] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul  2 13:21:15 water kernel: [    0.489785] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jul  2 13:21:15 water kernel: [    0.489810] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
Jul  2 13:21:15 water kernel: [    0.489985] hub 4-0:1.0: USB hub found
Jul  2 13:21:15 water kernel: [    0.489991] hub 4-0:1.0: 2 ports detected
Jul  2 13:21:15 water kernel: [    0.490152] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Jul  2 13:21:15 water kernel: [    0.500857] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul  2 13:21:15 water kernel: [    0.500880] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul  2 13:21:15 water kernel: [    0.501129] mousedev: PS/2 mouse device common for all mice
Jul  2 13:21:15 water kernel: [    0.501362] rtc_cmos 00:06: RTC can wake from S4
Jul  2 13:21:15 water kernel: [    0.501481] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Jul  2 13:21:15 water kernel: [    0.501503] rtc0: alarms up to one month, y3k, 114 bytes nvram
Jul  2 13:21:15 water kernel: [    0.501748] device-mapper: uevent: version 1.0.3
Jul  2 13:21:15 water kernel: [    0.501871] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
Jul  2 13:21:15 water kernel: [    0.502446] EISA: Probing bus 0 at eisa.0
Jul  2 13:21:15 water kernel: [    0.502455] Cannot allocate resource for EISA slot 1
Jul  2 13:21:15 water kernel: [    0.502460] Cannot allocate resource for EISA slot 2
Jul  2 13:21:15 water kernel: [    0.502463] Cannot allocate resource for EISA slot 3
Jul  2 13:21:15 water kernel: [    0.502466] Cannot allocate resource for EISA slot 4
Jul  2 13:21:15 water kernel: [    0.502469] Cannot allocate resource for EISA slot 5
Jul  2 13:21:15 water kernel: [    0.502471] Cannot allocate resource for EISA slot 6
Jul  2 13:21:15 water kernel: [    0.502474] Cannot allocate resource for EISA slot 7
Jul  2 13:21:15 water kernel: [    0.502477] Cannot allocate resource for EISA slot 8
Jul  2 13:21:15 water kernel: [    0.502480] EISA: Detected 0 cards.
Jul  2 13:21:15 water kernel: [    0.502497] cpufreq-nforce2: No nForce2 chipset.
Jul  2 13:21:15 water kernel: [    0.502552] cpuidle: using governor ladder
Jul  2 13:21:15 water kernel: [    0.502625] cpuidle: using governor menu
Jul  2 13:21:15 water kernel: [    0.502629] EFI Variables Facility v0.08 2004-May-17
Jul  2 13:21:15 water kernel: [    0.503639] TCP cubic registered
Jul  2 13:21:15 water kernel: [    0.503900] NET: Registered protocol family 10
Jul  2 13:21:15 water kernel: [    0.505111] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul  2 13:21:15 water kernel: [    0.508418] NET: Registered protocol family 17
Jul  2 13:21:15 water kernel: [    0.508482] Registering the dns_resolver key type
Jul  2 13:21:15 water kernel: [    0.508517] Using IPI No-Shortcut mode
Jul  2 13:21:15 water kernel: [    0.508668] PM: Hibernation image not present or could not be loaded.
Jul  2 13:21:15 water kernel: [    0.508685] registered taskstats version 1
Jul  2 13:21:15 water kernel: [    0.680990] ata2.01: NODEV after polling detection
Jul  2 13:21:15 water kernel: [    0.681212] ata1.00: HPA detected: current 151144863, native 156301488
Jul  2 13:21:15 water kernel: [    0.681222] ata1.00: ATA-6: IC25N080ATMR04-0, MO4OADEA, max UDMA/100
Jul  2 13:21:15 water kernel: [    0.681226] ata1.00: 151144863 sectors, multi 16: LBA 
Jul  2 13:21:15 water kernel: [    0.688790] ata2.00: ATAPI: UJDA745 DVD/CDRW, 1.03, max UDMA/33
Jul  2 13:21:15 water kernel: [    0.693115] ata1.00: configured for UDMA/100
Jul  2 13:21:15 water kernel: [    0.704768] ata2.00: configured for UDMA/33
Jul  2 13:21:15 water kernel: [    0.721547] ACPI: Battery Slot [BAT0] (battery present)
Jul  2 13:21:15 water kernel: [    0.852025] isapnp: No Plug & Play device found
Jul  2 13:21:15 water kernel: [    0.852333] scsi 0:0:0:0: Direct-Access     ATA      IC25N080ATMR04-0 MO4O PQ: 0 ANSI: 5
Jul  2 13:21:15 water kernel: [    0.852645] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul  2 13:21:15 water kernel: [    0.852891] sd 0:0:0:0: [sda] 151144863 512-byte logical blocks: (77.3 GB/72.0 GiB)
Jul  2 13:21:15 water kernel: [    0.852963] sd 0:0:0:0: [sda] Write Protect is off
Jul  2 13:21:15 water kernel: [    0.852968] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul  2 13:21:15 water kernel: [    0.852999] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  2 13:21:15 water kernel: [    0.856160] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA745 DVD/CDRW 1.03 PQ: 0 ANSI: 5
Jul  2 13:21:15 water kernel: [    0.859979] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jul  2 13:21:15 water kernel: [    0.859985] cdrom: Uniform CD-ROM driver Revision: 3.20
Jul  2 13:21:15 water kernel: [    0.860228] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jul  2 13:21:15 water kernel: [    0.860341] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul  2 13:21:15 water kernel: [    0.906429]  sda: sda1 sda2 < sda5 >
Jul  2 13:21:15 water kernel: [    0.906626] sda: p5 size 9762816 extends beyond EOD, enabling native capacity
Jul  2 13:21:15 water kernel: [    0.906705] ata1: soft resetting link
Jul  2 13:21:15 water kernel: [    1.065753] Freeing initrd memory: 13292k freed
Jul  2 13:21:15 water kernel: [    1.092592] ata1.00: n_sectors mismatch 151144863 != 156301488
Jul  2 13:21:15 water kernel: [    1.092597] ata1.00: new n_sectors matches native, probably late HPA unlock, n_sectors updated
Jul  2 13:21:15 water kernel: [    1.098135]   Magic number: 4:230:339
Jul  2 13:21:15 water kernel: [    1.098328] rtc_cmos 00:06: setting system clock to 2012-07-02 17:20:56 UTC (1341249656)
Jul  2 13:21:15 water kernel: [    1.099433] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul  2 13:21:15 water kernel: [    1.099436] EDD information not available.
Jul  2 13:21:15 water kernel: [    1.100062] usb 4-1: new full speed USB device number 2 using uhci_hcd
Jul  2 13:21:15 water kernel: [    1.108552] ata1.00: configured for UDMA/100
Jul  2 13:21:15 water kernel: [    1.108563] ata1: EH complete
Jul  2 13:21:15 water kernel: [    1.108668] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Jul  2 13:21:15 water kernel: [    1.109013] sda: detected capacity change from 77386169856 to 80026361856
Jul  2 13:21:15 water kernel: [    1.148340]  sda: sda1 sda2 < sda5 >
Jul  2 13:21:15 water kernel: [    1.148708] sd 0:0:0:0: [sda] Attached SCSI disk
Jul  2 13:21:15 water kernel: [    1.148755] Freeing unused kernel memory: 696k freed
Jul  2 13:21:15 water kernel: [    1.149226] Write protecting the kernel text: 5332k
Jul  2 13:21:15 water kernel: [    1.149277] Write protecting the kernel read-only data: 2188k
Jul  2 13:21:15 water kernel: [    1.335839] Floppy drive(s): fd0 is 1.44M
Jul  2 13:21:15 water kernel: [    1.356363] FDC 0 is a National Semiconductor PC87306
Jul  2 13:21:15 water kernel: [    1.443809] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
Jul  2 13:21:15 water kernel: [    1.443814] e1000: Copyright (c) 1999-2006 Intel Corporation.
Jul  2 13:21:15 water kernel: [    1.443875] e1000 0000:02:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:21:15 water kernel: [    1.744941] e1000 0000:02:01.0: eth0: (PCI:33MHz:32-bit) 00:0d:60:10:85:f6
Jul  2 13:21:15 water kernel: [    1.744955] e1000 0000:02:01.0: eth0: Intel(R) PRO/1000 Network Connection
Jul  2 13:21:15 water kernel: [    1.947078] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jul  2 13:21:15 water kernel: [   19.393710] lp: driver loaded but no devices found
Jul  2 13:21:15 water kernel: [   19.415866] Adding 4881404k swap on /dev/sda5.  Priority:-1 extents:1 across:4881404k 
Jul  2 13:21:15 water kernel: [   19.485670] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul  2 13:21:15 water kernel: [   19.619093] intel_rng: FWH not detected
Jul  2 13:21:15 water kernel: [   19.655495] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jul  2 13:21:15 water kernel: [   19.919555] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:0512]
Jul  2 13:21:15 water kernel: [   19.919575] yenta_cardbus 0000:02:00.0: Using INTVAL to route CSC interrupts to PCI
Jul  2 13:21:15 water kernel: [   19.919578] yenta_cardbus 0000:02:00.0: Routing CardBus interrupts to PCI
Jul  2 13:21:15 water kernel: [   19.919585] yenta_cardbus 0000:02:00.0: TI: mfunc 0x01d21022, devctl 0x64
Jul  2 13:21:15 water kernel: [   19.998976] type=1400 audit(1341249675.397:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=519 comm="apparmor_parser"
Jul  2 13:21:15 water kernel: [   19.999651] type=1400 audit(1341249675.397:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=519 comm="apparmor_parser"
Jul  2 13:21:15 water kernel: [   20.000140] type=1400 audit(1341249675.401:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=519 comm="apparmor_parser"
Jul  2 13:21:15 water modem-manager[522]: <info>  ModemManager (version 0.5) starting...
Jul  2 13:21:15 water avahi-daemon[524]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Jul  2 13:21:15 water avahi-daemon[524]: Successfully dropped root privileges.
Jul  2 13:21:15 water avahi-daemon[524]: avahi-daemon 0.6.30 starting up.
Jul  2 13:21:15 water NetworkManager[530]: <info> NetworkManager (version 0.9.1.90) is starting...
Jul  2 13:21:15 water NetworkManager[530]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin Gobi
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin X22X
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin ZTE
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin Ericsson MBM
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin Nokia
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin AnyData
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin Novatel
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin SimTech
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin Wavecom
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin MotoC
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin Sierra
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin Generic
Jul  2 13:21:15 water avahi-daemon[524]: Successfully called chroot().
Jul  2 13:21:15 water avahi-daemon[524]: Successfully dropped remaining capabilities.
Jul  2 13:21:15 water avahi-daemon[524]: Loading service file /services/udisks.service.
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin Option
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin Option High-Speed
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin Huawei
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin Longcheer
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin Samsung
Jul  2 13:21:15 water modem-manager[522]: <info>  Loaded plugin Linktop
Jul  2 13:21:15 water kernel: [   20.124923] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/LNXVIDEO:00/input/input4
Jul  2 13:21:15 water kernel: [   20.125154] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Jul  2 13:21:15 water kernel: [   20.129489] parport_pc 00:0b: reported by Plug and Play ACPI
Jul  2 13:21:15 water kernel: [   20.129535] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
Jul  2 13:21:15 water avahi-daemon[524]: Network interface enumeration completed.
Jul  2 13:21:15 water avahi-daemon[524]: Registering HINFO record with values 'I686'/'LINUX'.
Jul  2 13:21:15 water avahi-daemon[524]: Server startup complete. Host name is water.local. Local service cookie is 3021251816.
Jul  2 13:21:15 water avahi-daemon[524]: Service "water" (/services/udisks.service) successfully established.
Jul  2 13:21:15 water kernel: [   20.172465] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x0438, PCI irq 11
Jul  2 13:21:15 water kernel: [   20.172472] yenta_cardbus 0000:02:00.0: Socket status: 30000006
Jul  2 13:21:15 water kernel: [   20.172485] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge window: [io  0x4000-0x8fff]
Jul  2 13:21:15 water NetworkManager[530]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jul  2 13:21:15 water kernel: [   20.172490] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x8fff: excluding 0x4000-0x40ff 0x4400-0x44ff 0x4800-0x48ff 0x4c00-0x4cff
Jul  2 13:21:15 water kernel: [   20.365147] [drm] Initialized drm 1.1.0 20060810
Jul  2 13:21:15 water kernel: [   20.410468] Non-volatile memory driver v1.3
Jul  2 13:21:15 water dbus[501]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jul  2 13:21:15 water kernel: [   20.496363] lp0: using parport0 (interrupt-driven).
Jul  2 13:21:15 water kernel: [   20.498416] cfg80211: Calling CRDA to update world regulatory domain
Jul  2 13:21:15 water kernel: [   20.498677] irda_init()
Jul  2 13:21:15 water kernel: [   20.498697] NET: Registered protocol family 23
Jul  2 13:21:15 water kernel: [   20.504370] nsc-ircc 00:0c: [io  0x02f8-0x02ff]
Jul  2 13:21:15 water kernel: [   20.504439] nsc-ircc 00:0c: [irq 3]
Jul  2 13:21:15 water kernel: [   20.504445] nsc-ircc 00:0c: [dma 1]
Jul  2 13:21:15 water kernel: [   20.504908] nsc-ircc 00:0c: activated
Jul  2 13:21:15 water kernel: [   20.504914] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
Jul  2 13:21:15 water kernel: [   20.505120] nsc-ircc, chip->init
Jul  2 13:21:15 water kernel: [   20.505130] nsc-ircc, Found chip at base=0x02e
Jul  2 13:21:15 water kernel: [   20.505154] nsc-ircc, driver loaded (Dag Brattli)
Jul  2 13:21:15 water kernel: [   20.540673] IrDA: Registered device irda0
Jul  2 13:21:15 water kernel: [   20.540680] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
Jul  2 13:21:15 water polkitd[552]: started daemon version 0.102 using authority implementation `local' version `0.102'
Jul  2 13:21:15 water dbus[501]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jul  2 13:21:15 water NetworkManager[530]:    SCPlugin-Ifupdown: init!
Jul  2 13:21:15 water NetworkManager[530]:    SCPlugin-Ifupdown: update_system_hostname
Jul  2 13:21:15 water NetworkManager[530]:    SCPluginIfupdown: management mode: unmanaged
Jul  2 13:21:15 water NetworkManager[530]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0)
Jul  2 13:21:15 water NetworkManager[530]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul  2 13:21:15 water NetworkManager[530]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/irda0, iface: irda0)
Jul  2 13:21:15 water NetworkManager[530]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/irda0, iface: irda0): no ifupdown configuration found.
Jul  2 13:21:15 water NetworkManager[530]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul  2 13:21:15 water NetworkManager[530]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul  2 13:21:15 water NetworkManager[530]:    SCPlugin-Ifupdown: end _init.
Jul  2 13:21:15 water NetworkManager[530]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul  2 13:21:15 water NetworkManager[530]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul  2 13:21:15 water NetworkManager[530]:    Ifupdown: get unmanaged devices count: 0
Jul  2 13:21:15 water NetworkManager[530]:    SCPlugin-Ifupdown: (140114064) ... get_connections.
Jul  2 13:21:15 water NetworkManager[530]:    SCPlugin-Ifupdown: (140114064) ... get_connections (managed=false): return empty list.
Jul  2 13:21:15 water NetworkManager[530]:    keyfile: parsing cabin ... 
Jul  2 13:21:15 water NetworkManager[530]:    keyfile:     read connection 'cabin'
Jul  2 13:21:15 water kernel: [   20.555777]  0x8000-0x803f
Jul  2 13:21:15 water kernel: [   20.594746] Bluetooth: Core ver 2.16
Jul  2 13:21:15 water kernel: [   20.594831] NET: Registered protocol family 31
Jul  2 13:21:15 water kernel: [   20.594834] Bluetooth: HCI device and connection manager initialized
Jul  2 13:21:15 water kernel: [   20.594838] Bluetooth: HCI socket layer initialized
Jul  2 13:21:15 water kernel: [   20.594841] Bluetooth: L2CAP socket layer initialized
Jul  2 13:21:16 water kernel: [   20.600088] Bluetooth: SCO socket layer initialized
Jul  2 13:21:16 water kernel: [   20.603091] Bluetooth: Generic Bluetooth USB driver ver 0.6
Jul  2 13:21:16 water kernel: [   20.606635] usbcore: registered new interface driver btusb
Jul  2 13:21:16 water NetworkManager[530]:    Ifupdown: get unmanaged devices count: 0
Jul  2 13:21:16 water NetworkManager[530]: <info> modem-manager is now available
Jul  2 13:21:16 water NetworkManager[530]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul  2 13:21:16 water NetworkManager[530]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul  2 13:21:16 water NetworkManager[530]: <info> WWAN enabled by radio killswitch; enabled by state file
Jul  2 13:21:16 water NetworkManager[530]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul  2 13:21:16 water NetworkManager[530]: <info> Networking is enabled by state file
Jul  2 13:21:16 water NetworkManager[530]: <info> (eth0): carrier is OFF
Jul  2 13:21:16 water NetworkManager[530]: <info> (eth0): new Ethernet device (driver: 'e1000' ifindex: 2)
Jul  2 13:21:16 water NetworkManager[530]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul  2 13:21:16 water NetworkManager[530]: <info> (eth0): now managed
Jul  2 13:21:16 water NetworkManager[530]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul  2 13:21:16 water NetworkManager[530]: <info> (eth0): bringing up device.
Jul  2 13:21:16 water NetworkManager[530]: <info> (eth0): preparing device.
Jul  2 13:21:16 water NetworkManager[530]: <info> (eth0): deactivating device (reason 'managed') [2]
Jul  2 13:21:16 water kernel: [   20.664468] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  2 13:21:16 water NetworkManager[530]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0
Jul  2 13:21:16 water NetworkManager[530]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jul  2 13:21:16 water NetworkManager[530]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0)
Jul  2 13:21:16 water NetworkManager[530]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul  2 13:21:16 water kernel: [   20.753891] 
Jul  2 13:21:16 water kernel: [   20.753904] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge window: [mem 0xc0200000-0xcfffffff]
Jul  2 13:21:16 water kernel: [   20.753911] pcmcia_socket pcmcia_socket0: cs: memory probe 0xc0200000-0xcfffffff: excluding 0xc0200000-0xc09fffff 0xc3a00000-0xcc1fffff 0xcfa00000-0xd01fffff
Jul  2 13:21:16 water kernel: [   20.753941] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge window: [mem 0xe8000000-0xefffffff pref]
Jul  2 13:21:16 water kernel: [   20.753946] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe8000000-0xefffffff: excluding 0xe8000000-0xefffffff
Jul  2 13:21:16 water kernel: [   20.778496] yenta_cardbus 0000:02:00.1: CardBus bridge found [1014:0512]
Jul  2 13:21:16 water kernel: [   20.778517] yenta_cardbus 0000:02:00.1: Using INTVAL to route CSC interrupts to PCI
Jul  2 13:21:16 water kernel: [   20.778521] yenta_cardbus 0000:02:00.1: Routing CardBus interrupts to PCI
Jul  2 13:21:16 water kernel: [   20.778528] yenta_cardbus 0000:02:00.1: TI: mfunc 0x01d21022, devctl 0x64
Jul  2 13:21:16 water kernel: [   20.858257] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:21:16 water kernel: [   20.858299] Intel ICH 0000:00:1f.5: setting latency timer to 64
Jul  2 13:21:16 water udev-configure-printer: add /module/lp
Jul  2 13:21:16 water udev-configure-printer: Failed to get parent
Jul  2 13:21:16 water NetworkManager[530]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul  2 13:21:16 water NetworkManager[530]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul  2 13:21:16 water failsafe: Failsafe of 120 seconds reached.
Jul  2 13:21:16 water kernel: [   21.018608] yenta_cardbus 0000:02:00.1: ISA IRQ mask 0x0438, PCI irq 11
Jul  2 13:21:16 water kernel: [   21.018613] yenta_cardbus 0000:02:00.1: Socket status: 30000006
Jul  2 13:21:16 water kernel: [   21.018624] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge window: [io  0x4000-0x8fff]
Jul  2 13:21:16 water kernel: [   21.018629] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x8fff: excluding 0x4000-0x40ff 0x4400-0x44ff 0x4800-0x48ff 0x4c00-0x4cff
Jul  2 13:21:16 water kernel: [   21.223155] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0/0x0
Jul  2 13:21:16 water kernel: [   21.223168] serio: Synaptics pass-through port at isa0060/serio1/input0
Jul  2 13:21:16 water kernel: [   21.265216] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
Jul  2 13:21:16 water kernel: [   21.266631] [drm] radeon defaulting to kernel modesetting.
Jul  2 13:21:16 water kernel: [   21.266635] [drm] radeon kernel modesetting enabled.
Jul  2 13:21:16 water kernel: [   21.266757] radeon 0000:01:00.0: power state changed by ACPI to D0
Jul  2 13:21:16 water kernel: [   21.266763] radeon 0000:01:00.0: power state changed by ACPI to D0
Jul  2 13:21:16 water kernel: [   21.266776] radeon 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:21:16 water kernel: [   21.303795] thinkpad_acpi: ThinkPad ACPI Extras v0.24
Jul  2 13:21:16 water kernel: [   21.303801] thinkpad_acpi: http://ibm-acpi.sf.net/
Jul  2 13:21:16 water kernel: [   21.303804] thinkpad_acpi: ThinkPad BIOS 1RETDMWW (3.18 ), EC 1RHT71WW-3.04
Jul  2 13:21:16 water kernel: [   21.303807] thinkpad_acpi: IBM ThinkPad T40 , model 237392U
Jul  2 13:21:16 water kernel: [   21.303811] thinkpad_acpi: WARNING: Outdated ThinkPad BIOS/EC firmware
Jul  2 13:21:16 water kernel: [   21.303814] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
Jul  2 13:21:16 water kernel: [   21.305127] [drm] initializing kernel modesetting (RV250 0x1002:0x4C66 0x1014:0x0531).
Jul  2 13:21:16 water kernel: [   21.305161] [drm] register mmio base: 0xC0100000
Jul  2 13:21:16 water kernel: [   21.305164] [drm] register mmio size: 65536
Jul  2 13:21:16 water kernel: [   21.305448] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
Jul  2 13:21:16 water kernel: [   21.305467] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
Jul  2 13:21:16 water kernel: [   21.305507] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
Jul  2 13:21:16 water kernel: [   21.305536] radeon 0000:01:00.0: GTT: 256M 0xD0000000 - 0xDFFFFFFF
Jul  2 13:21:16 water kernel: [   21.305546] radeon 0000:01:00.0: VRAM: 128M 0x00000000E0000000 - 0x00000000E7FFFFFF (32M used)
Jul  2 13:21:16 water kernel: [   21.305563] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jul  2 13:21:16 water kernel: [   21.305566] [drm] Driver supports precise vblank timestamp query.
Jul  2 13:21:16 water kernel: [   21.305583] [drm] radeon: irq initialized.
Jul  2 13:21:16 water kernel: [   21.305973] [drm] Detected VRAM RAM=128M, BAR=128M
Jul  2 13:21:16 water kernel: [   21.305979] [drm] RAM width 64bits DDR
Jul  2 13:21:16 water kernel: [   21.311143] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
Jul  2 13:21:16 water kernel: [   21.323815] type=1400 audit(1341249676.721:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=705 comm="apparmor_parser"
Jul  2 13:21:16 water kernel: [   21.332705] type=1400 audit(1341249676.733:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=706 comm="apparmor_parser"
Jul  2 13:21:16 water kernel: [   21.336697] type=1400 audit(1341249676.737:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=706 comm="apparmor_parser"
Jul  2 13:21:16 water kernel: [   21.337130] type=1400 audit(1341249676.737:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=706 comm="apparmor_parser"
Jul  2 13:21:16 water kernel: [   21.350026] [TTM] Zone  kernel: Available graphics memory: 440360 kiB.
Jul  2 13:21:16 water kernel: [   21.350029] [TTM] Zone highmem: Available graphics memory: 771820 kiB.
Jul  2 13:21:16 water kernel: [   21.350032] [TTM] Initializing pool allocator.
Jul  2 13:21:16 water kernel: [   21.350072] [drm] radeon: 32M of VRAM memory ready
Jul  2 13:21:16 water kernel: [   21.350075] [drm] radeon: 256M of GTT memory ready.
Jul  2 13:21:16 water kernel: [   21.351228] radeon 0000:01:00.0: WB disabled
Jul  2 13:21:16 water kernel: [   21.377984] type=1400 audit(1341249676.777:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=708 comm="apparmor_parser"
Jul  2 13:21:16 water kernel: [   21.381944] [drm] Loading R200 Microcode
Jul  2 13:21:16 water kernel: [   21.390975] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
Jul  2 13:21:16 water kernel: [   21.396367] type=1400 audit(1341249676.797:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=708 comm="apparmor_parser"
Jul  2 13:21:16 water kernel: [   21.400336] Registered led device: tpacpi::thinklight
Jul  2 13:21:16 water kernel: [   21.401528] Registered led device: tpacpi::power
Jul  2 13:21:16 water kernel: [   21.402332] Registered led device: tpacpi::standby
Jul  2 13:21:16 water kernel: [   21.418871] type=1400 audit(1341249676.817:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=708 comm="apparmor_parser"
Jul  2 13:21:16 water kernel: [   21.457317]  0x8000-0x803f
Jul  2 13:21:16 water kernel: [   21.465606] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
Jul  2 13:21:16 water kernel: [   21.505053] 
Jul  2 13:21:16 water kernel: [   21.505066] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge window: [mem 0xc0200000-0xcfffffff]
Jul  2 13:21:16 water kernel: [   21.505073] pcmcia_socket pcmcia_socket1: cs: memory probe 0xc0200000-0xcfffffff: excluding 0xc0200000-0xc09fffff 0xc3a00000-0xcc1fffff 0xcfa00000-0xd01fffff
Jul  2 13:21:16 water kernel: [   21.505102] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge window: [mem 0xe8000000-0xefffffff pref]
Jul  2 13:21:16 water kernel: [   21.505107] pcmcia_socket pcmcia_socket1: cs: memory probe 0xe8000000-0xefffffff: excluding 0xe8000000-0xefffffff
Jul  2 13:21:16 water kernel: [   21.505407] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
Jul  2 13:21:17 water kernel: [   21.530160] ath5k 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:21:17 water acpid: starting up with proc fs
Jul  2 13:21:17 water acpid: 32 rules loaded
Jul  2 13:21:17 water acpid: waiting for events: event logging is off
Jul  2 13:21:17 water cron[781]: (CRON) INFO (pidfile fd = 3)
Jul  2 13:21:17 water anacron[804]: Anacron 2.3 started on 2012-07-02
Jul  2 13:21:17 water cron[810]: (CRON) STARTUP (fork ok)
Jul  2 13:21:17 water cron[810]: (CRON) INFO (Running @reboot jobs)
Jul  2 13:21:17 water anacron[804]: Will run job `cron.weekly' in 10 min.
Jul  2 13:21:17 water anacron[804]: Jobs will be executed sequentially
Jul  2 13:21:17 water NetworkManager[530]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/irda0, iface: irda0)
Jul  2 13:21:17 water NetworkManager[530]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/irda0, iface: irda0): no ifupdown configuration found.
Jul  2 13:21:17 water udev-configure-printer: add /devices/pnp0/00:0b/printer/lp0
Jul  2 13:21:17 water bluetoothd[859]: Bluetooth daemon 4.96
Jul  2 13:21:17 water udev-configure-printer: Failed to get parent
Jul  2 13:21:17 water kernel: [   21.530240] ath5k 0000:02:02.0: registered as 'phy0'
Jul  2 13:21:17 water kernel: [   21.956953] intel8x0_measure_ac97_clock: measured 54797 usecs (2640 samples)
Jul  2 13:21:17 water kernel: [   21.956959] intel8x0: clocking to 48000
Jul  2 13:21:17 water kernel: [   21.983753] init: failsafe main process (645) killed by TERM signal
Jul  2 13:21:17 water kernel: [   21.993149] init: apport pre-start process (771) terminated with status 1
Jul  2 13:21:17 water kernel: [   22.054517] init: apport post-stop process (801) terminated with status 1
Jul  2 13:21:17 water kernel: [   22.156093] ppdev: user-space parallel port driver
Jul  2 13:21:17 water kernel: [   22.258372] ath: EEPROM regdomain: 0x61
Jul  2 13:21:17 water kernel: [   22.258376] ath: EEPROM indicates we should expect a direct regpair map
Jul  2 13:21:17 water kernel: [   22.258383] ath: Country alpha2 being used: 00
Jul  2 13:21:17 water kernel: [   22.258385] ath: Regpair used: 0x61
Jul  2 13:21:17 water kernel: [   22.270622] cfg80211: World regulatory domain updated:
Jul  2 13:21:17 water kernel: [   22.270628] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul  2 13:21:17 water kernel: [   22.270632] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.270637] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.270641] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.270645] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.270649] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.294633] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294639] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.294643] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294647] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.294650] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294655] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.294658] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294662] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.294666] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294670] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.294674] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294678] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.294681] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294686] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.294689] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294693] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:21:17 water bluetoothd[859]: Starting SDP server
Jul  2 13:21:17 water kernel: [   22.294697] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294701] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.294704] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294709] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.294712] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294716] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.294720] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294724] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.294727] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294732] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.294735] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294739] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:21:17 water kernel: [   22.294743] cfg80211: Disabling freq 5040 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jul  2 13:21:17 water kernel: [   22.294747] cfg80211: Disabling freq 5060 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jul  2 13:21:17 water kernel: [   22.294751] cfg80211: Disabling freq 5080 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jul  2 13:21:17 water kernel: [   22.294755] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294759] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294762] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294767] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294770] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294774] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294778] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294782] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294786] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294790] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294793] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294798] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294801] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294805] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294809] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294813] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294816] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294821] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294824] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294828] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294832] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294836] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294840] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294844] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294847] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294852] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294855] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294859] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294863] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294867] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294871] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294875] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294878] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294882] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294886] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294890] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294894] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294898] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294901] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294906] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294909] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294913] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294917] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294921] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294925] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294929] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.294932] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:21:17 water kernel: [   22.294937] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:21:17 water kernel: [   22.306435] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Jul  2 13:21:17 water kernel: [   22.332776] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jul  2 13:21:17 water kernel: [   22.336133] Registered led device: ath5k-phy0::rx
Jul  2 13:21:17 water kernel: [   22.336203] Registered led device: ath5k-phy0::tx
Jul  2 13:21:17 water kernel: [   22.336223] ath5k phy0: Atheros AR5211 chip found (MAC: 0x42, PHY: 0x30)
Jul  2 13:21:17 water kernel: [   22.336226] ath5k phy0: RF5111 5GHz radio found (0x17)
Jul  2 13:21:17 water kernel: [   22.336230] ath5k phy0: RF2111 2GHz radio found (0x23)
Jul  2 13:21:17 water kernel: [   22.400004] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377
Jul  2 13:21:17 water kernel: [   22.421689] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
Jul  2 13:21:17 water kernel: [   22.422164] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Jul  2 13:21:17 water kernel: [   22.422556] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Jul  2 13:21:17 water kernel: [   22.422983] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xdc000-0xfffff
Jul  2 13:21:17 water kernel: [   22.423052] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Jul  2 13:21:17 water kernel: [   22.423121] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x600fffff
Jul  2 13:21:17 water kernel: [   22.423197] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Jul  2 13:21:17 water kernel: [   22.432660] [drm] radeon: ring at 0x00000000D0001000
Jul  2 13:21:17 water kernel: [   22.432685] [drm] ring test succeeded in 1 usecs
Jul  2 13:21:17 water kernel: [   22.432993] [drm] radeon: ib pool ready.
Jul  2 13:21:17 water kernel: [   22.433116] [drm] ib test succeeded in 0 usecs
Jul  2 13:21:17 water kernel: [   22.435010] [drm] Panel ID String: SXGA+ Single (85MHz)    
Jul  2 13:21:17 water kernel: [   22.435015] [drm] Panel Size 1400x1050
Jul  2 13:21:17 water kernel: [   22.446135] [drm] radeon legacy LVDS backlight initialized
Jul  2 13:21:17 water kernel: [   22.476901] Bluetooth: RFCOMM TTY layer initialized
Jul  2 13:21:17 water kernel: [   22.476910] Bluetooth: RFCOMM socket layer initialized
Jul  2 13:21:17 water kernel: [   22.476913] Bluetooth: RFCOMM ver 1.11
Jul  2 13:21:17 water kernel: [   22.516628] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377
Jul  2 13:21:17 water kernel: [   22.559386] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
Jul  2 13:21:17 water kernel: [   22.559848] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff:
Jul  2 13:21:17 water kernel: [   22.571886] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul  2 13:21:17 water kernel: [   22.571891] Bluetooth: BNEP filters: protocol multicast
Jul  2 13:21:17 water bluetoothd[859]: Listening for HCI events on hci0
Jul  2 13:21:17 water bluetoothd[859]: HCI dev 0 up
Jul  2 13:21:17 water NetworkManager[530]: <warn> bluez error getting default adapter: No such adapter
Jul  2 13:21:17 water kernel: [   22.582098]  clean.
Jul  2 13:21:17 water NetworkManager[530]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/ieee80211/phy0/rfkill2) (driver (unknown))
Jul  2 13:21:17 water bluetoothd[859]: Adapter /org/bluez/859/hci0 has been enabled
Jul  2 13:21:18 water kernel: [   22.582268] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7:
Jul  2 13:21:18 water kernel: [   22.606849] [drm] No TV DAC info found in BIOS
Jul  2 13:21:18 water kernel: [   22.612297] [drm] Radeon Display Connectors
Jul  2 13:21:18 water kernel: [   22.612302] [drm] Connector 0:
Jul  2 13:21:18 water kernel: [   22.612305] [drm]   VGA
Jul  2 13:21:18 water kernel: [   22.612309] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
Jul  2 13:21:18 water kernel: [   22.612311] [drm]   Encoders:
Jul  2 13:21:18 water kernel: [   22.612314] [drm]     CRT1: INTERNAL_DAC1
Jul  2 13:21:18 water kernel: [   22.612316] [drm] Connector 1:
Jul  2 13:21:18 water kernel: [   22.612318] [drm]   DVI-D
Jul  2 13:21:18 water kernel: [   22.612321] [drm]   HPD1
Jul  2 13:21:18 water kernel: [   22.612324] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Jul  2 13:21:18 water kernel: [   22.612326] [drm]   Encoders:
Jul  2 13:21:18 water kernel: [   22.612329] [drm]     DFP1: INTERNAL_TMDS1
Jul  2 13:21:18 water kernel: [   22.612331] [drm] Connector 2:
Jul  2 13:21:18 water kernel: [   22.612333] [drm]   LVDS
Jul  2 13:21:18 water kernel: [   22.612335] [drm]   Encoders:
Jul  2 13:21:18 water kernel: [   22.612337] [drm]     LCD1: INTERNAL_LVDS
Jul  2 13:21:18 water kernel: [   22.612339] [drm] Connector 3:
Jul  2 13:21:18 water kernel: [   22.612341] [drm]   S-video
Jul  2 13:21:18 water kernel: [   22.612343] [drm]   Encoders:
Jul  2 13:21:18 water kernel: [   22.612345] [drm]     TV1: INTERNAL_DAC2
Jul  2 13:21:18 water kernel: [   22.620407]  clean.
Jul  2 13:21:18 water kernel: [   22.620538] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xdc000-0xfffff
Jul  2 13:21:18 water kernel: [   22.620610] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Jul  2 13:21:18 water kernel: [   22.620680] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x600fffff
Jul  2 13:21:18 water kernel: [   22.620757] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
Jul  2 13:21:18 water bluetoothd[859]: Inquiry Cancel Failed with status 0x0c
Jul  2 13:21:18 water NetworkManager[530]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jul  2 13:21:18 water NetworkManager[530]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 4)
Jul  2 13:21:18 water NetworkManager[530]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul  2 13:21:18 water NetworkManager[530]: <info> (wlan0): now managed
Jul  2 13:21:18 water NetworkManager[530]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul  2 13:21:18 water NetworkManager[530]: <info> (wlan0): bringing up device.
Jul  2 13:21:18 water NetworkManager[530]: <info> (wlan0): preparing device.
Jul  2 13:21:18 water kernel: [   22.790974] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
Jul  2 13:21:18 water kernel: [   22.807121] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  2 13:21:18 water NetworkManager[530]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jul  2 13:21:18 water dbus[501]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jul  2 13:21:18 water NetworkManager[530]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wlan0, iface: wlan0)
Jul  2 13:21:18 water NetworkManager[530]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul  2 13:21:18 water dbus[501]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jul  2 13:21:18 water NetworkManager[530]: <info> wpa_supplicant started
Jul  2 13:21:18 water kernel: [   22.851655] [drm] Radeon display connector DVI-D-1: No monitor connected or invalid EDID
Jul  2 13:21:18 water NetworkManager[530]: <info> (wlan0): supplicant interface state: starting -> ready
Jul  2 13:21:18 water NetworkManager[530]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul  2 13:21:18 water NetworkManager[530]: <info> (wlan0): supplicant interface state: ready -> inactive
Jul  2 13:21:18 water kernel: [   22.851703] [drm] radeon: power management initialized
Jul  2 13:21:18 water kernel: [   22.921247] [drm] fb mappable at 0xE0040000
Jul  2 13:21:18 water kernel: [   22.921253] [drm] vram apper at 0xE0000000
Jul  2 13:21:18 water kernel: [   22.921256] [drm] size 1478656
Jul  2 13:21:18 water kernel: [   22.921258] [drm] fb depth is 8
Jul  2 13:21:18 water kernel: [   22.921261] [drm]    pitch is 1408
Jul  2 13:21:18 water kernel: [   22.921608] fbcon: radeondrmfb (fb0) is primary device
Jul  2 13:21:18 water kernel: [   22.924676] Console: switching to colour frame buffer device 175x65
Jul  2 13:21:18 water kernel: [   22.924751] fb0: radeondrmfb frame buffer device
Jul  2 13:21:18 water kernel: [   22.924754] drm: registered panic notifier
Jul  2 13:21:18 water kernel: [   22.924771] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:00.0 on minor 0
Jul  2 13:21:18 water acpid: client connected from 996[0:0]
Jul  2 13:21:18 water acpid: 1 client rule loaded
Jul  2 13:21:19 water udev-configure-printer: add /devices/pnp0/00:0b/printer/lp0
Jul  2 13:21:19 water udev-configure-printer: Failed to get parent
Jul  2 13:21:19 water udev-configure-printer: add /module/lp
Jul  2 13:21:19 water udev-configure-printer: Failed to get parent
Jul  2 13:21:19 water dbus[501]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jul  2 13:21:19 water dbus[501]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jul  2 13:21:19 water accounts-daemon[1006]: started daemon version 0.6.14
Jul  2 13:21:19 water kernel: [   23.959271] psmouse serio2: ID: 10 00 64
Jul  2 13:21:19 water dbus[501]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jul  2 13:21:19 water dbus[501]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jul  2 13:21:20 water dbus[501]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jul  2 13:21:20 water dbus[501]: [system] Successfully activated service 'org.freedesktop.UPower'
Jul  2 13:21:20 water kernel: [   25.172486] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jul  2 13:21:21 water kernel: [   25.624506] init: plymouth-stop pre-start process (1181) terminated with status 1
Jul  2 13:21:21 water dbus[501]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jul  2 13:21:21 water dbus[501]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jul  2 13:21:22 water dbus[501]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jul  2 13:21:22 water dbus[501]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jul  2 17:21:22 water rtkit-daemon[1224]: Successfully called chroot.
Jul  2 17:21:22 water rtkit-daemon[1224]: Successfully dropped privileges.
Jul  2 17:21:22 water rtkit-daemon[1224]: Successfully limited resources.
Jul  2 17:21:22 water rtkit-daemon[1224]: Running.
Jul  2 17:21:22 water rtkit-daemon[1224]: Watchdog thread running.
Jul  2 17:21:22 water rtkit-daemon[1224]: Canary thread running.
Jul  2 17:21:22 water rtkit-daemon[1224]: Successfully made thread 1221 of process 1221 (n/a) owned by '104' high priority at nice level -11.
Jul  2 17:21:22 water rtkit-daemon[1224]: Supervising 1 threads of 1 processes of 1 users.
Jul  2 17:21:22 water rtkit-daemon[1224]: Successfully made thread 1228 of process 1221 (n/a) owned by '104' RT at priority 5.
Jul  2 17:21:22 water rtkit-daemon[1224]: Supervising 2 threads of 1 processes of 1 users.
Jul  2 17:21:22 water rtkit-daemon[1224]: Successfully made thread 1229 of process 1221 (n/a) owned by '104' RT at priority 5.
Jul  2 17:21:22 water rtkit-daemon[1224]: Supervising 3 threads of 1 processes of 1 users.
Jul  2 13:21:22 water pulseaudio[1221]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Jul  2 13:21:22 water pulseaudio[1221]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Jul  2 13:21:22 water pulseaudio[1221]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Jul  2 13:21:22  pulseaudio[1221]: last message repeated 2 times
Jul  2 13:21:22 water kernel: [   27.327847] IBM TrackPoint firmware: 0x0e, buttons: 3/3
Jul  2 13:21:22 water kernel: [   27.566454] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input7
Jul  2 13:21:46 water gnome-session[1261]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1
Jul  2 17:21:47 water rtkit-daemon[1224]: Successfully made thread 1348 of process 1348 (n/a) owned by '1000' high priority at nice level -11.
Jul  2 17:21:47 water rtkit-daemon[1224]: Supervising 4 threads of 2 processes of 2 users.
Jul  2 17:21:47 water rtkit-daemon[1224]: Successfully made thread 1349 of process 1348 (n/a) owned by '1000' RT at priority 5.
Jul  2 17:21:47 water rtkit-daemon[1224]: Supervising 5 threads of 2 processes of 2 users.
Jul  2 17:21:47 water rtkit-daemon[1224]: Successfully made thread 1350 of process 1348 (n/a) owned by '1000' RT at priority 5.
Jul  2 17:21:47 water rtkit-daemon[1224]: Supervising 6 threads of 2 processes of 2 users.
Jul  2 13:21:47 water pulseaudio[1348]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Jul  2 13:21:47 water pulseaudio[1348]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Jul  2 13:21:47 water pulseaudio[1348]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Jul  2 13:21:49  pulseaudio[1348]: last message repeated 2 times
Jul  2 13:21:49 water dbus[501]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jul  2 13:21:49 water dbus[501]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jul  2 13:22:51 water dbus[501]: [system] Activating service name='org.debian.apt' (using servicehelper)
Jul  2 13:22:53 water AptDaemon: INFO: Initializing daemon
Jul  2 13:22:53 water dbus[501]: [system] Successfully activated service 'org.debian.apt'
Jul  2 13:22:53 water AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Jul  2 13:22:53 water AptDaemon.Trans: INFO: Simulate was called
Jul  2 13:22:53 water AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/817c1a138136405bbd51f97c5768dfdf
Jul  2 13:22:55 water dbus[501]: [system] Activating service name='com.ubuntu.SystemService' (using servicehelper)
Jul  2 13:22:56 water dbus[501]: [system] Successfully activated service 'com.ubuntu.SystemService'
Jul  2 13:23:00 water AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Jul  2 13:25:02 water kernel: [  247.262024] Critical temperature reached (94 C), shutting down.
Jul  2 13:25:02 water kernel: Kernel logging (proc) stopped.
Jul  2 13:25:02 water rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="494" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jul  2 13:28:37 water kernel: imklog 5.8.1, log source = /proc/kmsg started.
Jul  2 13:28:37 water rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="504" x-info="http://www.rsyslog.com"] start
Jul  2 13:28:37 water rsyslogd: rsyslogd's groupid changed to 103
Jul  2 13:28:37 water rsyslogd: rsyslogd's userid changed to 101
Jul  2 13:28:37 water rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul  2 13:28:37 water kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  2 13:28:37 water kernel: [    0.000000] Initializing cgroup subsys cpu
Jul  2 13:28:37 water kernel: [    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
Jul  2 13:28:37 water kernel: [    0.000000] KERNEL supported cpus:
Jul  2 13:28:37 water kernel: [    0.000000]   Intel GenuineIntel
Jul  2 13:28:37 water kernel: [    0.000000]   AMD AuthenticAMD
Jul  2 13:28:37 water kernel: [    0.000000]   NSC Geode by NSC
Jul  2 13:28:37 water kernel: [    0.000000]   Cyrix CyrixInstead
Jul  2 13:28:37 water kernel: [    0.000000]   Centaur CentaurHauls
Jul  2 13:28:37 water kernel: [    0.000000]   Transmeta GenuineTMx86
Jul  2 13:28:37 water kernel: [    0.000000]   Transmeta TransmetaCPU
Jul  2 13:28:37 water kernel: [    0.000000]   UMC UMC UMC UMC
Jul  2 13:28:37 water kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  2 13:28:37 water kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jul  2 13:28:37 water kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jul  2 13:28:37 water kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Jul  2 13:28:37 water kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Jul  2 13:28:37 water kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000005ff60000 (usable)
Jul  2 13:28:37 water kernel: [    0.000000]  BIOS-e820: 000000005ff60000 - 000000005ff77000 (ACPI data)
Jul  2 13:28:37 water kernel: [    0.000000]  BIOS-e820: 000000005ff77000 - 000000005ff79000 (ACPI NVS)
Jul  2 13:28:37 water kernel: [    0.000000]  BIOS-e820: 000000005ff80000 - 0000000060000000 (reserved)
Jul  2 13:28:37 water kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
Jul  2 13:28:37 water kernel: [    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
Jul  2 13:28:37 water kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Jul  2 13:28:37 water kernel: [    0.000000] DMI present.
Jul  2 13:28:37 water kernel: [    0.000000] DMI: IBM 237392U/237392U, BIOS 1RETDMWW (3.18 ) 09/15/2005
Jul  2 13:28:37 water kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jul  2 13:28:37 water kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jul  2 13:28:37 water kernel: [    0.000000] last_pfn = 0x5ff60 max_arch_pfn = 0x100000
Jul  2 13:28:37 water kernel: [    0.000000] MTRR default type: uncachable
Jul  2 13:28:37 water kernel: [    0.000000] MTRR fixed ranges enabled:
Jul  2 13:28:37 water kernel: [    0.000000]   00000-9FFFF write-back
Jul  2 13:28:37 water kernel: [    0.000000]   A0000-BFFFF uncachable
Jul  2 13:28:37 water kernel: [    0.000000]   C0000-CFFFF write-protect
Jul  2 13:28:37 water kernel: [    0.000000]   D0000-DBFFF uncachable
Jul  2 13:28:37 water kernel: [    0.000000]   DC000-DFFFF write-back
Jul  2 13:28:37 water kernel: [    0.000000]   E0000-FFFFF write-protect
Jul  2 13:28:37 water kernel: [    0.000000] MTRR variable ranges enabled:
Jul  2 13:28:37 water kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Jul  2 13:28:37 water kernel: [    0.000000]   1 base 040000000 mask FE0000000 write-back
Jul  2 13:28:37 water kernel: [    0.000000]   2 base 05FF80000 mask FFFF80000 uncachable
Jul  2 13:28:37 water kernel: [    0.000000]   3 disabled
Jul  2 13:28:37 water kernel: [    0.000000]   4 disabled
Jul  2 13:28:37 water kernel: [    0.000000]   5 disabled
Jul  2 13:28:37 water kernel: [    0.000000]   6 disabled
Jul  2 13:28:37 water kernel: [    0.000000]   7 disabled
Jul  2 13:28:37 water kernel: [    0.000000] PAT not supported by CPU.
Jul  2 13:28:37 water kernel: [    0.000000] original variable MTRRs
Jul  2 13:28:37 water kernel: [    0.000000] reg 0, base: 0GB, range: 1GB, type WB
Jul  2 13:28:37 water kernel: [    0.000000] reg 1, base: 1GB, range: 512MB, type WB
Jul  2 13:28:37 water kernel: [    0.000000] reg 2, base: 1572352KB, range: 512KB, type UC
Jul  2 13:28:37 water kernel: [    0.000000] total RAM covered: 1535M
Jul  2 13:28:37 water kernel: [    0.000000] Found optimal setting for mtrr clean up
Jul  2 13:28:37 water kernel: [    0.000000]  gran_size: 64K 	chunk_size: 1M 	num_reg: 3  	lose cover RAM: 0G
Jul  2 13:28:37 water kernel: [    0.000000] New variable MTRRs
Jul  2 13:28:37 water kernel: [    0.000000] reg 0, base: 0GB, range: 1GB, type WB
Jul  2 13:28:37 water kernel: [    0.000000] reg 1, base: 1GB, range: 512MB, type WB
Jul  2 13:28:37 water kernel: [    0.000000] reg 2, base: 1572352KB, range: 512KB, type UC
Jul  2 13:28:37 water kernel: [    0.000000] initial memory mapped : 0 - 01c00000
Jul  2 13:28:37 water kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Jul  2 13:28:37 water kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jul  2 13:28:37 water kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Jul  2 13:28:37 water kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Jul  2 13:28:37 water kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Jul  2 13:28:37 water kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
Jul  2 13:28:37 water kernel: [    0.000000] RAMDISK: 365fa000 - 372f5000
Jul  2 13:28:37 water kernel: [    0.000000] ACPI: RSDP 000f6d70 00024 (v02 IBM   )
Jul  2 13:28:37 water kernel: [    0.000000] ACPI: XSDT 5ff6a6cd 0004C (v01 IBM    TP-1R    00003180  LTP 00000000)
Jul  2 13:28:37 water kernel: [    0.000000] ACPI: FACP 5ff6a800 000F4 (v03 IBM    TP-1R    00003180 IBM  00000001)
Jul  2 13:28:37 water kernel: [    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 (20110413/tbfadt-529)
Jul  2 13:28:37 water kernel: [    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 0x000000000000102C/0x0 (20110413/tbfadt-560)
Jul  2 13:28:37 water kernel: [    0.000000] ACPI: DSDT 5ff6a9e7 0C4D5 (v01 IBM    TP-1R    00003180 MSFT 0100000E)
Jul  2 13:28:37 water kernel: [    0.000000] ACPI: FACS 5ff78000 00040
Jul  2 13:28:37 water kernel: [    0.000000] ACPI: SSDT 5ff6a9b4 00033 (v01 IBM    TP-1R    00003180 MSFT 0100000E)
Jul  2 13:28:37 water kernel: [    0.000000] ACPI: ECDT 5ff76ebc 00052 (v01 IBM    TP-1R    00003180 IBM  00000001)
Jul  2 13:28:37 water kernel: [    0.000000] ACPI: TCPA 5ff76f0e 00032 (v01 IBM    TP-1R    00003180 PTL  00000001)
Jul  2 13:28:37 water kernel: [    0.000000] ACPI: BOOT 5ff76fd8 00028 (v01 IBM    TP-1R    00003180  LTP 00000001)
Jul  2 13:28:37 water kernel: [    0.000000] 647MB HIGHMEM available.
Jul  2 13:28:37 water kernel: [    0.000000] 887MB LOWMEM available.
Jul  2 13:28:37 water kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jul  2 13:28:37 water kernel: [    0.000000]   low ram: 0 - 377fe000
Jul  2 13:28:37 water kernel: [    0.000000] Zone PFN ranges:
Jul  2 13:28:37 water kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jul  2 13:28:37 water kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jul  2 13:28:37 water kernel: [    0.000000]   HighMem  0x000377fe -> 0x0005ff60
Jul  2 13:28:37 water kernel: [    0.000000] Movable zone start PFN for each node
Jul  2 13:28:37 water kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul  2 13:28:37 water kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jul  2 13:28:37 water kernel: [    0.000000]     0: 0x00000100 -> 0x0005ff60
Jul  2 13:28:37 water kernel: [    0.000000] On node 0 totalpages: 392943
Jul  2 13:28:37 water kernel: [    0.000000] free_area_init_node: node 0, pgdat c17b11c0, node_mem_map f59fa200
Jul  2 13:28:37 water kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul  2 13:28:37 water kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul  2 13:28:37 water kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jul  2 13:28:37 water kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jul  2 13:28:37 water kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Jul  2 13:28:37 water kernel: [    0.000000]   HighMem zone: 1295 pages used for memmap
Jul  2 13:28:37 water kernel: [    0.000000]   HighMem zone: 164435 pages, LIFO batch:31
Jul  2 13:28:37 water kernel: [    0.000000] Using APIC driver default
Jul  2 13:28:37 water kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul  2 13:28:37 water kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jul  2 13:28:37 water kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Jul  2 13:28:37 water kernel: [    0.000000] APIC: disable apic facility
Jul  2 13:28:37 water kernel: [    0.000000] APIC: switched to apic NOOP
Jul  2 13:28:37 water kernel: [    0.000000] nr_irqs_gsi: 16
Jul  2 13:28:37 water kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul  2 13:28:37 water kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jul  2 13:28:37 water kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jul  2 13:28:37 water kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jul  2 13:28:37 water kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Jul  2 13:28:37 water kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 60000000:9f800000)
Jul  2 13:28:37 water kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul  2 13:28:37 water kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Jul  2 13:28:37 water kernel: [    0.000000] PERCPU: Embedded 12 pages/cpu @f5400000 s26240 r0 d22912 u4194304
Jul  2 13:28:37 water kernel: [    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
Jul  2 13:28:37 water kernel: [    0.000000] pcpu-alloc: [0] 0 
Jul  2 13:28:37 water kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 389872
Jul  2 13:28:37 water kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=6df79d67-e791-4ac7-a601-04b274f7b6fd ro quiet splash vt.handoff=7
Jul  2 13:28:37 water kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul  2 13:28:37 water kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul  2 13:28:37 water kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul  2 13:28:37 water kernel: [    0.000000] Initializing CPU#0
Jul  2 13:28:37 water kernel: [    0.000000] allocated 6288640 bytes of page_cgroup
Jul  2 13:28:37 water kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul  2 13:28:37 water kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0005ff60)
Jul  2 13:28:37 water kernel: [    0.000000] Memory: 1529628k/1572224k available (5329k kernel code, 42144k reserved, 2589k data, 696k init, 662920k highmem)
Jul  2 13:28:37 water kernel: [    0.000000] virtual kernel memory layout:
Jul  2 13:28:37 water kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Jul  2 13:28:37 water kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul  2 13:28:37 water kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jul  2 13:28:37 water kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jul  2 13:28:37 water kernel: [    0.000000]       .init : 0xc17bc000 - 0xc186a000   ( 696 kB)
Jul  2 13:28:37 water kernel: [    0.000000]       .data : 0xc1534784 - 0xc17bbd80   (2589 kB)
Jul  2 13:28:37 water kernel: [    0.000000]       .text : 0xc1000000 - 0xc1534784   (5329 kB)
Jul  2 13:28:37 water kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul  2 13:28:37 water kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Jul  2 13:28:37 water kernel: [    0.000000] Hierarchical RCU implementation.
Jul  2 13:28:37 water kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jul  2 13:28:37 water kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256 16
Jul  2 13:28:37 water kernel: [    0.000000] CPU 0 irqstacks, hard=f4806000 soft=f4808000
Jul  2 13:28:37 water kernel: [    0.000000] Extended CMOS year: 2000
Jul  2 13:28:37 water kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jul  2 13:28:37 water kernel: [    0.000000] Console: colour dummy device 80x25
Jul  2 13:28:37 water kernel: [    0.000000] console [tty0] enabled
Jul  2 13:28:37 water kernel: [    0.000000] Fast TSC calibration using PIT
Jul  2 13:28:37 water kernel: [    0.000000] Detected 1594.768 MHz processor.
Jul  2 13:28:37 water kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3189.53 BogoMIPS (lpj=6379072)
Jul  2 13:28:37 water kernel: [    0.004013] pid_max: default: 32768 minimum: 301
Jul  2 13:28:37 water kernel: [    0.004051] Security Framework initialized
Jul  2 13:28:37 water kernel: [    0.004093] AppArmor: AppArmor initialized
Jul  2 13:28:37 water kernel: [    0.004096] Yama: becoming mindful.
Jul  2 13:28:37 water kernel: [    0.004197] Mount-cache hash table entries: 512
Jul  2 13:28:37 water kernel: [    0.004424] Initializing cgroup subsys cpuacct
Jul  2 13:28:37 water kernel: [    0.004435] Initializing cgroup subsys memory
Jul  2 13:28:37 water kernel: [    0.004449] Initializing cgroup subsys devices
Jul  2 13:28:37 water kernel: [    0.004453] Initializing cgroup subsys freezer
Jul  2 13:28:37 water kernel: [    0.004456] Initializing cgroup subsys net_cls
Jul  2 13:28:37 water kernel: [    0.004460] Initializing cgroup subsys blkio
Jul  2 13:28:37 water kernel: [    0.004472] Initializing cgroup subsys perf_event
Jul  2 13:28:37 water kernel: [    0.004526] mce: CPU supports 5 MCE banks
Jul  2 13:28:37 water kernel: [    0.004834] SMP alternatives: switching to UP code
Jul  2 13:28:37 water kernel: [    0.014647] Freeing SMP alternatives: 24k freed
Jul  2 13:28:37 water kernel: [    0.014661] ACPI: Core revision 20110413
Jul  2 13:28:37 water kernel: [    0.021963] ACPI: setting ELCR to 0200 (from 0800)
Jul  2 13:28:37 water kernel: [    0.024022] ftrace: allocating 24885 entries in 49 pages
Jul  2 13:28:37 water kernel: [    0.028144] weird, boot CPU (#0) not listed by the BIOS.
Jul  2 13:28:37 water kernel: [    0.028149] SMP motherboard not detected.
Jul  2 13:28:37 water kernel: [    0.028152] Local APIC not detected. Using dummy APIC emulation.
Jul  2 13:28:37 water kernel: [    0.028155] SMP disabled
Jul  2 13:28:37 water kernel: [    0.028158] Performance Events: 
Jul  2 13:28:37 water kernel: [    0.028162] no APIC, boot with the "lapic" boot parameter to force-enable it.
Jul  2 13:28:37 water kernel: [    0.028164] no hardware sampling interrupt available.
Jul  2 13:28:37 water kernel: [    0.028169] p6 PMU driver.
Jul  2 13:28:37 water kernel: [    0.028176] ... version:                0
Jul  2 13:28:37 water kernel: [    0.028178] ... bit width:              32
Jul  2 13:28:37 water kernel: [    0.028180] ... generic registers:      2
Jul  2 13:28:37 water kernel: [    0.028183] ... value mask:             00000000ffffffff
Jul  2 13:28:37 water kernel: [    0.028185] ... max period:             000000007fffffff
Jul  2 13:28:37 water kernel: [    0.028187] ... fixed-purpose events:   0
Jul  2 13:28:37 water kernel: [    0.028190] ... event mask:             0000000000000003
Jul  2 13:28:37 water kernel: [    0.028847] Brought up 1 CPUs
Jul  2 13:28:37 water kernel: [    0.028852] Total of 1 processors activated (3189.53 BogoMIPS).
Jul  2 13:28:37 water kernel: [    0.029066] devtmpfs: initialized
Jul  2 13:28:37 water kernel: [    0.029332] PM: Registering ACPI NVS region at 5ff77000 (8192 bytes)
Jul  2 13:28:37 water kernel: [    0.035866] print_constraints: dummy: 
Jul  2 13:28:37 water kernel: [    0.035894] Time: 17:28:17  Date: 07/02/12
Jul  2 13:28:37 water kernel: [    0.035962] NET: Registered protocol family 16
Jul  2 13:28:37 water kernel: [    0.036173] EISA bus registered
Jul  2 13:28:37 water kernel: [    0.036192] ACPI: bus type pci registered
Jul  2 13:28:37 water kernel: [    0.036598] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=8
Jul  2 13:28:37 water kernel: [    0.036601] PCI: Using configuration type 1 for base access
Jul  2 13:28:37 water kernel: [    0.038087] bio: create slab <bio-0> at 0
Jul  2 13:28:37 water kernel: [    0.040304] ACPI: EC: EC description table is found, configuring boot EC
Jul  2 13:28:37 water kernel: [    0.052498] ACPI: Interpreter enabled
Jul  2 13:28:37 water kernel: [    0.052505] ACPI: (supports S0 S3 S4 S5)
Jul  2 13:28:37 water kernel: [    0.052533] ACPI: Using PIC for interrupt routing
Jul  2 13:28:37 water kernel: [    0.056462] ACPI: Power Resource [PUBS] (on)
Jul  2 13:28:37 water kernel: [    0.060493] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Jul  2 13:28:37 water kernel: [    0.061030] ACPI: ACPI Dock Station Driver: 3 docks/bays found
Jul  2 13:28:37 water kernel: [    0.061030] HEST: Table not found.
Jul  2 13:28:37 water kernel: [    0.061030] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Jul  2 13:28:37 water kernel: [    0.061030] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul  2 13:28:37 water kernel: [    0.061030] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Jul  2 13:28:37 water kernel: [    0.061030] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Jul  2 13:28:37 water kernel: [    0.061030] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Jul  2 13:28:37 water kernel: [    0.061030] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
Jul  2 13:28:37 water kernel: [    0.061030] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
Jul  2 13:28:37 water kernel: [    0.061030] pci_root PNP0A03:00: host bridge window [mem 0x60000000-0xfebfffff] (ignored)
Jul  2 13:28:37 water kernel: [    0.061030] pci 0000:00:00.0: [8086:3340] type 0 class 0x000600
Jul  2 13:28:37 water kernel: [    0.061030] pci 0000:00:00.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
Jul  2 13:28:37 water kernel: [    0.061030] pci 0000:00:01.0: [8086:3341] type 1 class 0x000604
Jul  2 13:28:37 water kernel: [    0.061035] pci 0000:00:1d.0: [8086:24c2] type 0 class 0x000c03
Jul  2 13:28:37 water kernel: [    0.061081] pci 0000:00:1d.0: reg 20: [io  0x1800-0x181f]
Jul  2 13:28:37 water kernel: [    0.061117] pci 0000:00:1d.1: [8086:24c4] type 0 class 0x000c03
Jul  2 13:28:37 water kernel: [    0.061163] pci 0000:00:1d.1: reg 20: [io  0x1820-0x183f]
Jul  2 13:28:37 water kernel: [    0.061200] pci 0000:00:1d.2: [8086:24c7] type 0 class 0x000c03
Jul  2 13:28:37 water kernel: [    0.061246] pci 0000:00:1d.2: reg 20: [io  0x1840-0x185f]
Jul  2 13:28:37 water kernel: [    0.061293] pci 0000:00:1d.7: [8086:24cd] type 0 class 0x000c03
Jul  2 13:28:37 water kernel: [    0.061316] pci 0000:00:1d.7: reg 10: [mem 0xc0000000-0xc00003ff]
Jul  2 13:28:37 water kernel: [    0.061398] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jul  2 13:28:37 water kernel: [    0.061404] pci 0000:00:1d.7: PME# disabled
Jul  2 13:28:37 water kernel: [    0.061424] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
Jul  2 13:28:37 water kernel: [    0.061468] pci 0000:00:1f.0: [8086:24cc] type 0 class 0x000601
Jul  2 13:28:37 water kernel: [    0.061537] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH4 ACPI/GPIO/TCO
Jul  2 13:28:37 water kernel: [    0.061544] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH4 GPIO
Jul  2 13:28:37 water kernel: [    0.061561] pci 0000:00:1f.1: [8086:24ca] type 0 class 0x000101
Jul  2 13:28:37 water kernel: [    0.061576] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
Jul  2 13:28:37 water kernel: [    0.061587] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
Jul  2 13:28:37 water kernel: [    0.061599] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
Jul  2 13:28:37 water kernel: [    0.061610] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
Jul  2 13:28:37 water kernel: [    0.061621] pci 0000:00:1f.1: reg 20: [io  0x1860-0x186f]
Jul  2 13:28:37 water kernel: [    0.061633] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
Jul  2 13:28:37 water kernel: [    0.061662] pci 0000:00:1f.3: [8086:24c3] type 0 class 0x000c05
Jul  2 13:28:37 water kernel: [    0.061709] pci 0000:00:1f.3: reg 20: [io  0x1880-0x189f]
Jul  2 13:28:37 water kernel: [    0.061747] pci 0000:00:1f.5: [8086:24c5] type 0 class 0x000401
Jul  2 13:28:37 water kernel: [    0.061764] pci 0000:00:1f.5: reg 10: [io  0x1c00-0x1cff]
Jul  2 13:28:37 water kernel: [    0.061774] pci 0000:00:1f.5: reg 14: [io  0x18c0-0x18ff]
Jul  2 13:28:37 water kernel: [    0.061785] pci 0000:00:1f.5: reg 18: [mem 0xc0000c00-0xc0000dff]
Jul  2 13:28:37 water kernel: [    0.061796] pci 0000:00:1f.5: reg 1c: [mem 0xc0000800-0xc00008ff]
Jul  2 13:28:37 water kernel: [    0.061835] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Jul  2 13:28:37 water kernel: [    0.061841] pci 0000:00:1f.5: PME# disabled
Jul  2 13:28:37 water kernel: [    0.061858] pci 0000:00:1f.6: [8086:24c6] type 0 class 0x000703
Jul  2 13:28:37 water kernel: [    0.061875] pci 0000:00:1f.6: reg 10: [io  0x2400-0x24ff]
Jul  2 13:28:37 water kernel: [    0.061886] pci 0000:00:1f.6: reg 14: [io  0x2000-0x207f]
Jul  2 13:28:37 water kernel: [    0.061939] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
Jul  2 13:28:37 water kernel: [    0.061944] pci 0000:00:1f.6: PME# disabled
Jul  2 13:28:37 water kernel: [    0.061973] pci 0000:01:00.0: [1002:4c66] type 0 class 0x000300
Jul  2 13:28:37 water kernel: [    0.061989] pci 0000:01:00.0: reg 10: [mem 0xe0000000-0xe7ffffff pref]
Jul  2 13:28:37 water kernel: [    0.061998] pci 0000:01:00.0: reg 14: [io  0x3000-0x30ff]
Jul  2 13:28:37 water kernel: [    0.062007] pci 0000:01:00.0: reg 18: [mem 0xc0100000-0xc010ffff]
Jul  2 13:28:37 water kernel: [    0.062033] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Jul  2 13:28:37 water kernel: [    0.062053] pci 0000:01:00.0: supports D1 D2
Jul  2 13:28:37 water kernel: [    0.062090] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jul  2 13:28:37 water kernel: [    0.062095] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
Jul  2 13:28:37 water kernel: [    0.062099] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
Jul  2 13:28:37 water kernel: [    0.062104] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe7ffffff pref]
Jul  2 13:28:37 water kernel: [    0.062131] pci 0000:02:00.0: [104c:ac55] type 2 class 0x000607
Jul  2 13:28:37 water kernel: [    0.062149] pci 0000:02:00.0: reg 10: [mem 0xb0000000-0xb0000fff]
Jul  2 13:28:37 water kernel: [    0.062170] pci 0000:02:00.0: supports D1 D2
Jul  2 13:28:37 water kernel: [    0.062173] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  2 13:28:37 water kernel: [    0.062179] pci 0000:02:00.0: PME# disabled
Jul  2 13:28:37 water kernel: [    0.062198] pci 0000:02:00.1: [104c:ac55] type 2 class 0x000607
Jul  2 13:28:37 water kernel: [    0.062216] pci 0000:02:00.1: reg 10: [mem 0xb1000000-0xb1000fff]
Jul  2 13:28:37 water kernel: [    0.062236] pci 0000:02:00.1: supports D1 D2
Jul  2 13:28:37 water kernel: [    0.062240] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot D3cold
Jul  2 13:28:37 water kernel: [    0.062245] pci 0000:02:00.1: PME# disabled
Jul  2 13:28:37 water kernel: [    0.062273] pci 0000:02:01.0: [8086:101e] type 0 class 0x000200
Jul  2 13:28:37 water kernel: [    0.062294] pci 0000:02:01.0: reg 10: [mem 0xc0220000-0xc023ffff]
Jul  2 13:28:37 water kernel: [    0.062305] pci 0000:02:01.0: reg 14: [mem 0xc0200000-0xc020ffff]
Jul  2 13:28:37 water kernel: [    0.062316] pci 0000:02:01.0: reg 18: [io  0x8000-0x803f]
Jul  2 13:28:37 water kernel: [    0.062349] pci 0000:02:01.0: reg 30: [mem 0x00000000-0x0000ffff pref]
Jul  2 13:28:37 water kernel: [    0.062374] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
Jul  2 13:28:37 water kernel: [    0.062379] pci 0000:02:01.0: PME# disabled
Jul  2 13:28:37 water kernel: [    0.062400] pci 0000:02:02.0: [168c:0012] type 0 class 0x000200
Jul  2 13:28:37 water kernel: [    0.062418] pci 0000:02:02.0: reg 10: [mem 0xc0210000-0xc021ffff]
Jul  2 13:28:37 water kernel: [    0.062521] pci 0000:00:1e.0: PCI bridge to [bus 02-08] (subtractive decode)
Jul  2 13:28:37 water kernel: [    0.062527] pci 0000:00:1e.0:   bridge window [io  0x4000-0x8fff]
Jul  2 13:28:37 water kernel: [    0.062533] pci 0000:00:1e.0:   bridge window [mem 0xc0200000-0xcfffffff]
Jul  2 13:28:37 water kernel: [    0.062539] pci 0000:00:1e.0:   bridge window [mem 0xe8000000-0xefffffff pref]
Jul  2 13:28:37 water kernel: [    0.062543] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Jul  2 13:28:37 water kernel: [    0.062547] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
Jul  2 13:28:37 water kernel: [    0.062628] pci_bus 0000:00: on NUMA node 0
Jul  2 13:28:37 water kernel: [    0.062632] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul  2 13:28:37 water kernel: [    0.062687] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Jul  2 13:28:37 water kernel: [    0.064021] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Jul  2 13:28:37 water kernel: [    0.064135]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
Jul  2 13:28:37 water kernel: [    0.067406] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:28:37 water kernel: [    0.067514] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:28:37 water kernel: [    0.067618] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:28:37 water kernel: [    0.067721] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:28:37 water kernel: [    0.067804] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Jul  2 13:28:37 water kernel: [    0.067889] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Jul  2 13:28:37 water kernel: [    0.067973] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Jul  2 13:28:37 water kernel: [    0.068090] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
Jul  2 13:28:37 water kernel: [    0.068239] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jul  2 13:28:37 water kernel: [    0.068244] vgaarb: loaded
Jul  2 13:28:37 water kernel: [    0.068247] vgaarb: bridge control possible 0000:01:00.0
Jul  2 13:28:37 water kernel: [    0.068588] SCSI subsystem initialized
Jul  2 13:28:37 water kernel: [    0.068678] libata version 3.00 loaded.
Jul  2 13:28:37 water kernel: [    0.068750] usbcore: registered new interface driver usbfs
Jul  2 13:28:37 water kernel: [    0.068767] usbcore: registered new interface driver hub
Jul  2 13:28:37 water kernel: [    0.068804] usbcore: registered new device driver usb
Jul  2 13:28:37 water kernel: [    0.068926] PCI: Using ACPI for IRQ routing
Jul  2 13:28:37 water kernel: [    0.069065] PCI: pci_cache_line_size set to 64 bytes
Jul  2 13:28:37 water kernel: [    0.069135] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
Jul  2 13:28:37 water kernel: [    0.069138] reserve RAM buffer: 000000005ff60000 - 000000005fffffff 
Jul  2 13:28:37 water kernel: [    0.069297] NetLabel: Initializing
Jul  2 13:28:37 water kernel: [    0.069300] NetLabel:  domain hash size = 128
Jul  2 13:28:37 water kernel: [    0.069302] NetLabel:  protocols = UNLABELED CIPSOv4
Jul  2 13:28:37 water kernel: [    0.069319] NetLabel:  unlabeled traffic allowed by default
Jul  2 13:28:37 water kernel: [    0.069386] Switching to clocksource pit
Jul  2 13:28:37 water kernel: [    0.079688] AppArmor: AppArmor Filesystem Enabled
Jul  2 13:28:37 water kernel: [    0.079756] pnp: PnP ACPI init
Jul  2 13:28:37 water kernel: [    0.079790] ACPI: bus type pnp registered
Jul  2 13:28:37 water kernel: [    0.080482] pnp 00:00: [mem 0x00000000-0x0009ffff]
Jul  2 13:28:37 water kernel: [    0.080487] pnp 00:00: [mem 0x000c0000-0x000c3fff]
Jul  2 13:28:37 water kernel: [    0.080490] pnp 00:00: [mem 0x000c4000-0x000c7fff]
Jul  2 13:28:37 water kernel: [    0.080494] pnp 00:00: [mem 0x000c8000-0x000cbfff]
Jul  2 13:28:37 water kernel: [    0.080497] pnp 00:00: [mem 0x000cc000-0x000cffff]
Jul  2 13:28:37 water kernel: [    0.080500] pnp 00:00: [mem 0x000d0000-0x000d3fff]
Jul  2 13:28:37 water kernel: [    0.080504] pnp 00:00: [mem 0x000d4000-0x000d3fff disabled]
Jul  2 13:28:37 water kernel: [    0.080507] pnp 00:00: [mem 0x000d8000-0x000d7fff disabled]
Jul  2 13:28:37 water kernel: [    0.080511] pnp 00:00: [mem 0x000dc000-0x000dffff]
Jul  2 13:28:37 water kernel: [    0.080514] pnp 00:00: [mem 0x000e0000-0x000e3fff]
Jul  2 13:28:37 water kernel: [    0.080518] pnp 00:00: [mem 0x000e4000-0x000e7fff]
Jul  2 13:28:37 water kernel: [    0.080521] pnp 00:00: [mem 0x000e8000-0x000ebfff]
Jul  2 13:28:37 water kernel: [    0.080524] pnp 00:00: [mem 0x000ec000-0x000effff]
Jul  2 13:28:37 water kernel: [    0.080527] pnp 00:00: [mem 0x000f0000-0x000fffff]
Jul  2 13:28:37 water kernel: [    0.080541] pnp 00:00: [mem 0x00100000-0x5fffffff]
Jul  2 13:28:37 water kernel: [    0.080544] pnp 00:00: [mem 0xfec00000-0xffffffff]
Jul  2 13:28:37 water kernel: [    0.080667] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
Jul  2 13:28:37 water kernel: [    0.080672] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
Jul  2 13:28:37 water kernel: [    0.080677] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
Jul  2 13:28:37 water kernel: [    0.080681] system 00:00: [mem 0x000c8000-0x000cbfff] could not be reserved
Jul  2 13:28:37 water kernel: [    0.080685] system 00:00: [mem 0x000cc000-0x000cffff] could not be reserved
Jul  2 13:28:37 water kernel: [    0.080690] system 00:00: [mem 0x000d0000-0x000d3fff] could not be reserved
Jul  2 13:28:37 water kernel: [    0.080694] system 00:00: [mem 0x000dc000-0x000dffff] could not be reserved
Jul  2 13:28:37 water kernel: [    0.080698] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
Jul  2 13:28:37 water kernel: [    0.080703] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
Jul  2 13:28:37 water kernel: [    0.080707] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
Jul  2 13:28:37 water kernel: [    0.080711] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
Jul  2 13:28:37 water kernel: [    0.080716] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
Jul  2 13:28:37 water kernel: [    0.080720] system 00:00: [mem 0x00100000-0x5fffffff] could not be reserved
Jul  2 13:28:37 water kernel: [    0.080725] system 00:00: [mem 0xfec00000-0xffffffff] could not be reserved
Jul  2 13:28:37 water kernel: [    0.080731] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Jul  2 13:28:37 water kernel: [    0.080770] pnp 00:01: [bus 00-ff]
Jul  2 13:28:37 water kernel: [    0.080774] pnp 00:01: [io  0x0cf8-0x0cff]
Jul  2 13:28:37 water kernel: [    0.080778] pnp 00:01: [io  0x0000-0x0cf7 window]
Jul  2 13:28:37 water kernel: [    0.080782] pnp 00:01: [io  0x0d00-0xffff window]
Jul  2 13:28:37 water kernel: [    0.080785] pnp 00:01: [mem 0x000a0000-0x000bffff window]
Jul  2 13:28:37 water kernel: [    0.080789] pnp 00:01: [mem 0x000c0000-0x000c3fff window]
Jul  2 13:28:37 water kernel: [    0.080792] pnp 00:01: [mem 0x000c4000-0x000c7fff window]
Jul  2 13:28:37 water kernel: [    0.080796] pnp 00:01: [mem 0x000c8000-0x000cbfff window]
Jul  2 13:28:37 water kernel: [    0.080800] pnp 00:01: [mem 0x000cc000-0x000cffff window]
Jul  2 13:28:37 water kernel: [    0.080803] pnp 00:01: [mem 0x000d0000-0x000d3fff window]
Jul  2 13:28:37 water kernel: [    0.080807] pnp 00:01: [mem 0x000d4000-0x000d7fff window]
Jul  2 13:28:37 water kernel: [    0.080810] pnp 00:01: [mem 0x000d8000-0x000dbfff window]
Jul  2 13:28:37 water kernel: [    0.080814] pnp 00:01: [mem 0x000dc000-0x000dffff window]
Jul  2 13:28:37 water kernel: [    0.080817] pnp 00:01: [mem 0x000e0000-0x000e3fff window]
Jul  2 13:28:37 water kernel: [    0.080821] pnp 00:01: [mem 0x000e4000-0x000e7fff window]
Jul  2 13:28:37 water kernel: [    0.080824] pnp 00:01: [mem 0x000e8000-0x000ebfff window]
Jul  2 13:28:37 water kernel: [    0.080828] pnp 00:01: [mem 0x000ec000-0x000effff window]
Jul  2 13:28:37 water kernel: [    0.080832] pnp 00:01: [mem 0x60000000-0xfebfffff window]
Jul  2 13:28:37 water kernel: [    0.080910] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
Jul  2 13:28:37 water kernel: [    0.081033] pnp 00:02: [io  0x0010-0x001f]
Jul  2 13:28:37 water kernel: [    0.081037] pnp 00:02: [io  0x0090-0x009f]
Jul  2 13:28:37 water kernel: [    0.081040] pnp 00:02: [io  0x0024-0x0025]
Jul  2 13:28:37 water kernel: [    0.081043] pnp 00:02: [io  0x0028-0x0029]
Jul  2 13:28:37 water kernel: [    0.081046] pnp 00:02: [io  0x002c-0x002d]
Jul  2 13:28:37 water kernel: [    0.081049] pnp 00:02: [io  0x0030-0x0031]
Jul  2 13:28:37 water kernel: [    0.081052] pnp 00:02: [io  0x0034-0x0035]
Jul  2 13:28:37 water kernel: [    0.081055] pnp 00:02: [io  0x0038-0x0039]
Jul  2 13:28:37 water kernel: [    0.081058] pnp 00:02: [io  0x003c-0x003d]
Jul  2 13:28:37 water kernel: [    0.081061] pnp 00:02: [io  0x00a4-0x00a5]
Jul  2 13:28:37 water kernel: [    0.081064] pnp 00:02: [io  0x00a8-0x00a9]
Jul  2 13:28:37 water kernel: [    0.081067] pnp 00:02: [io  0x00ac-0x00ad]
Jul  2 13:28:37 water kernel: [    0.081070] pnp 00:02: [io  0x00b0-0x00b5]
Jul  2 13:28:37 water kernel: [    0.081073] pnp 00:02: [io  0x00b8-0x00b9]
Jul  2 13:28:37 water kernel: [    0.081076] pnp 00:02: [io  0x00bc-0x00bd]
Jul  2 13:28:37 water kernel: [    0.081079] pnp 00:02: [io  0x0050-0x0053]
Jul  2 13:28:37 water kernel: [    0.081083] pnp 00:02: [io  0x0072-0x0077]
Jul  2 13:28:37 water kernel: [    0.081086] pnp 00:02: [io  0x002e-0x002f]
Jul  2 13:28:37 water kernel: [    0.081089] pnp 00:02: [io  0x1000-0x107f]
Jul  2 13:28:37 water kernel: [    0.081092] pnp 00:02: [io  0x1180-0x11bf]
Jul  2 13:28:37 water kernel: [    0.081095] pnp 00:02: [io  0x15e0-0x15ef]
Jul  2 13:28:37 water kernel: [    0.081098] pnp 00:02: [io  0x1600-0x162f]
Jul  2 13:28:37 water kernel: [    0.081101] pnp 00:02: [io  0x1632-0x167f]
Jul  2 13:28:37 water kernel: [    0.081104] pnp 00:02: [io  0x004e-0x004f]
Jul  2 13:28:37 water kernel: [    0.081107] pnp 00:02: [io  0x1630-0x1631]
Jul  2 13:28:37 water kernel: [    0.081197] system 00:02: [io  0x1000-0x107f] has been reserved
Jul  2 13:28:37 water kernel: [    0.081201] system 00:02: [io  0x1180-0x11bf] has been reserved
Jul  2 13:28:37 water kernel: [    0.081205] system 00:02: [io  0x15e0-0x15ef] has been reserved
Jul  2 13:28:37 water kernel: [    0.081209] system 00:02: [io  0x1600-0x162f] has been reserved
Jul  2 13:28:37 water kernel: [    0.081213] system 00:02: [io  0x1632-0x167f] has been reserved
Jul  2 13:28:37 water kernel: [    0.081218] system 00:02: [io  0x1630-0x1631] has been reserved
Jul  2 13:28:37 water kernel: [    0.081222] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul  2 13:28:37 water kernel: [    0.081243] pnp 00:03: [io  0x0000-0x000f]
Jul  2 13:28:37 water kernel: [    0.081246] pnp 00:03: [io  0x0080-0x008f]
Jul  2 13:28:37 water kernel: [    0.081249] pnp 00:03: [io  0x00c0-0x00df]
Jul  2 13:28:37 water kernel: [    0.081253] pnp 00:03: [dma 4]
Jul  2 13:28:37 water kernel: [    0.081290] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Jul  2 13:28:37 water kernel: [    0.081303] pnp 00:04: [io  0x0061]
Jul  2 13:28:37 water kernel: [    0.081339] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Jul  2 13:28:37 water kernel: [    0.081352] pnp 00:05: [io  0x00f0]
Jul  2 13:28:37 water kernel: [    0.081358] pnp 00:05: [irq 13]
Jul  2 13:28:37 water kernel: [    0.081402] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Jul  2 13:28:37 water kernel: [    0.081416] pnp 00:06: [io  0x0070-0x0071]
Jul  2 13:28:37 water kernel: [    0.081419] pnp 00:06: [irq 8]
Jul  2 13:28:37 water kernel: [    0.081456] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul  2 13:28:37 water avahi-daemon[516]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Jul  2 13:28:37 water avahi-daemon[516]: Successfully dropped root privileges.
Jul  2 13:28:37 water avahi-daemon[516]: avahi-daemon 0.6.30 starting up.
Jul  2 13:28:37 water avahi-daemon[516]: Successfully called chroot().
Jul  2 13:28:37 water avahi-daemon[516]: Successfully dropped remaining capabilities.
Jul  2 13:28:37 water avahi-daemon[516]: Loading service file /services/udisks.service.
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin Gobi
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin X22X
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin ZTE
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin Ericsson MBM
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin Nokia
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin AnyData
Jul  2 13:28:37 water avahi-daemon[516]: Network interface enumeration completed.
Jul  2 13:28:37 water avahi-daemon[516]: Registering HINFO record with values 'I686'/'LINUX'.
Jul  2 13:28:37 water avahi-daemon[516]: Server startup complete. Host name is water.local. Local service cookie is 977917914.
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin Novatel
Jul  2 13:28:37 water avahi-daemon[516]: Service "water" (/services/udisks.service) successfully established.
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin SimTech
Jul  2 13:28:37 water kernel: [    0.081470] pnp 00:07: [io  0x0060]
Jul  2 13:28:37 water kernel: [    0.081473] pnp 00:07: [io  0x0064]
Jul  2 13:28:37 water kernel: [    0.081476] pnp 00:07: [irq 1]
Jul  2 13:28:37 water kernel: [    0.081513] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
Jul  2 13:28:37 water kernel: [    0.081526] pnp 00:08: [irq 12]
Jul  2 13:28:37 water kernel: [    0.081565] pnp 00:08: Plug and Play ACPI device, IDs IBM0057 PNP0f13 (active)
Jul  2 13:28:37 water kernel: [    0.081612] pnp 00:09: [io  0x03f0-0x03f5]
Jul  2 13:28:37 water kernel: [    0.081616] pnp 00:09: [io  0x03f7]
Jul  2 13:28:37 water kernel: [    0.081619] pnp 00:09: [irq 6]
Jul  2 13:28:37 water kernel: [    0.081622] pnp 00:09: [dma 2]
Jul  2 13:28:37 water kernel: [    0.081684] pnp 00:09: Plug and Play ACPI device, IDs PNP0700 (active)
Jul  2 13:28:37 water kernel: [    0.081814] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (disabled)
Jul  2 13:28:37 water kernel: [    0.081939] pnp 00:0b: [io  0x03bc-0x03be]
Jul  2 13:28:37 water kernel: [    0.081943] pnp 00:0b: [irq 7]
Jul  2 13:28:37 water kernel: [    0.082036] pnp 00:0b: Plug and Play ACPI device, IDs PNP0400 (active)
Jul  2 13:28:37 water kernel: [    0.082196] pnp 00:0c: Plug and Play ACPI device, IDs IBM0071 PNP0511 (disabled)
Jul  2 13:28:37 water kernel: [    0.082864] pnp: PnP ACPI: found 13 devices
Jul  2 13:28:37 water kernel: [    0.082867] ACPI: ACPI bus type pnp unregistered
Jul  2 13:28:37 water kernel: [    0.082873] PnPBIOS: Disabled by ACPI PNP
Jul  2 13:28:37 water kernel: [    0.119815] Switching to clocksource acpi_pm
Jul  2 13:28:37 water kernel: [    0.119853] PCI: max bus depth: 2 pci_try_num: 3
Jul  2 13:28:37 water kernel: [    0.119885] pci 0000:00:1f.1: BAR 5: assigned [mem 0x60000000-0x600003ff]
Jul  2 13:28:37 water kernel: [    0.119894] pci 0000:00:1f.1: BAR 5: set to [mem 0x60000000-0x600003ff] (PCI address [0x60000000-0x600003ff])
Jul  2 13:28:37 water kernel: [    0.119901] pci 0000:01:00.0: BAR 6: assigned [mem 0xc0120000-0xc013ffff pref]
Jul  2 13:28:37 water kernel: [    0.119905] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jul  2 13:28:37 water kernel: [    0.119910] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
Jul  2 13:28:37 water kernel: [    0.119915] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
Jul  2 13:28:37 water kernel: [    0.119920] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe7ffffff pref]
Jul  2 13:28:37 water kernel: [    0.119930] pci 0000:02:00.0: BAR 15: assigned [mem 0xe8000000-0xebffffff pref]
Jul  2 13:28:37 water kernel: [    0.119935] pci 0000:02:00.0: BAR 16: assigned [mem 0xc4000000-0xc7ffffff]
Jul  2 13:28:37 water kernel: [    0.119939] pci 0000:02:00.1: BAR 15: assigned [mem 0xec000000-0xefffffff pref]
Jul  2 13:28:37 water kernel: [    0.119943] pci 0000:02:00.1: BAR 16: assigned [mem 0xc8000000-0xcbffffff]
Jul  2 13:28:37 water kernel: [    0.119948] pci 0000:02:01.0: BAR 6: assigned [mem 0xc0240000-0xc024ffff pref]
Jul  2 13:28:37 water kernel: [    0.119953] pci 0000:02:00.0: BAR 13: assigned [io  0x4000-0x40ff]
Jul  2 13:28:37 water kernel: [    0.119956] pci 0000:02:00.0: BAR 14: assigned [io  0x4400-0x44ff]
Jul  2 13:28:37 water kernel: [    0.119960] pci 0000:02:00.1: BAR 13: assigned [io  0x4800-0x48ff]
Jul  2 13:28:37 water kernel: [    0.119964] pci 0000:02:00.1: BAR 14: assigned [io  0x4c00-0x4cff]
Jul  2 13:28:37 water kernel: [    0.119968] pci 0000:02:00.0: CardBus bridge to [bus 03-06]
Jul  2 13:28:37 water kernel: [    0.119972] pci 0000:02:00.0:   bridge window [io  0x4000-0x40ff]
Jul  2 13:28:37 water kernel: [    0.119978] pci 0000:02:00.0:   bridge window [io  0x4400-0x44ff]
Jul  2 13:28:37 water kernel: [    0.119983] pci 0000:02:00.0:   bridge window [mem 0xe8000000-0xebffffff pref]
Jul  2 13:28:37 water kernel: [    0.119989] pci 0000:02:00.0:   bridge window [mem 0xc4000000-0xc7ffffff]
Jul  2 13:28:37 water kernel: [    0.119995] pci 0000:02:00.1: CardBus bridge to [bus 07-07]
Jul  2 13:28:37 water kernel: [    0.119999] pci 0000:02:00.1:   bridge window [io  0x4800-0x48ff]
Jul  2 13:28:37 water kernel: [    0.120004] pci 0000:02:00.1:   bridge window [io  0x4c00-0x4cff]
Jul  2 13:28:37 water kernel: [    0.120010] pci 0000:02:00.1:   bridge window [mem 0xec000000-0xefffffff pref]
Jul  2 13:28:37 water kernel: [    0.120016] pci 0000:02:00.1:   bridge window [mem 0xc8000000-0xcbffffff]
Jul  2 13:28:37 water kernel: [    0.120022] pci 0000:00:1e.0: PCI bridge to [bus 02-08]
Jul  2 13:28:37 water kernel: [    0.120026] pci 0000:00:1e.0:   bridge window [io  0x4000-0x8fff]
Jul  2 13:28:37 water kernel: [    0.120033] pci 0000:00:1e.0:   bridge window [mem 0xc0200000-0xcfffffff]
Jul  2 13:28:37 water kernel: [    0.120039] pci 0000:00:1e.0:   bridge window [mem 0xe8000000-0xefffffff pref]
Jul  2 13:28:37 water kernel: [    0.120061] pci 0000:00:1e.0: setting latency timer to 64
Jul  2 13:28:37 water kernel: [    0.120296] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Jul  2 13:28:37 water kernel: [    0.120301] PCI: setting IRQ 11 as level-triggered
Jul  2 13:28:37 water kernel: [    0.120308] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:28:37 water kernel: [    0.120492] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Jul  2 13:28:37 water kernel: [    0.120497] pci 0000:02:00.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:28:37 water kernel: [    0.120505] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Jul  2 13:28:37 water kernel: [    0.120509] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
Jul  2 13:28:37 water kernel: [    0.120513] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
Jul  2 13:28:37 water kernel: [    0.120517] pci_bus 0000:01: resource 1 [mem 0xc0100000-0xc01fffff]
Jul  2 13:28:37 water kernel: [    0.120521] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xe7ffffff pref]
Jul  2 13:28:37 water kernel: [    0.120525] pci_bus 0000:02: resource 0 [io  0x4000-0x8fff]
Jul  2 13:28:37 water kernel: [    0.120528] pci_bus 0000:02: resource 1 [mem 0xc0200000-0xcfffffff]
Jul  2 13:28:37 water kernel: [    0.120532] pci_bus 0000:02: resource 2 [mem 0xe8000000-0xefffffff pref]
Jul  2 13:28:37 water kernel: [    0.120536] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
Jul  2 13:28:37 water kernel: [    0.120540] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
Jul  2 13:28:37 water kernel: [    0.120544] pci_bus 0000:03: resource 0 [io  0x4000-0x40ff]
Jul  2 13:28:37 water kernel: [    0.120547] pci_bus 0000:03: resource 1 [io  0x4400-0x44ff]
Jul  2 13:28:37 water kernel: [    0.120551] pci_bus 0000:03: resource 2 [mem 0xe8000000-0xebffffff pref]
Jul  2 13:28:37 water kernel: [    0.120555] pci_bus 0000:03: resource 3 [mem 0xc4000000-0xc7ffffff]
Jul  2 13:28:37 water kernel: [    0.120559] pci_bus 0000:07: resource 0 [io  0x4800-0x48ff]
Jul  2 13:28:37 water kernel: [    0.120563] pci_bus 0000:07: resource 1 [io  0x4c00-0x4cff]
Jul  2 13:28:37 water kernel: [    0.120566] pci_bus 0000:07: resource 2 [mem 0xec000000-0xefffffff pref]
Jul  2 13:28:37 water kernel: [    0.120570] pci_bus 0000:07: resource 3 [mem 0xc8000000-0xcbffffff]
Jul  2 13:28:37 water kernel: [    0.120651] NET: Registered protocol family 2
Jul  2 13:28:37 water kernel: [    0.120753] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul  2 13:28:37 water kernel: [    0.121164] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul  2 13:28:37 water kernel: [    0.122672] Switched to NOHz mode on CPU #0
Jul  2 13:28:37 water kernel: [    0.123099] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul  2 13:28:37 water kernel: [    0.124270] TCP: Hash tables configured (established 131072 bind 65536)
Jul  2 13:28:37 water kernel: [    0.124276] TCP reno registered
Jul  2 13:28:37 water kernel: [    0.124287] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jul  2 13:28:37 water kernel: [    0.124325] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jul  2 13:28:37 water kernel: [    0.124569] NET: Registered protocol family 1
Jul  2 13:28:37 water kernel: [    0.124704] pci 0000:01:00.0: Boot video device
Jul  2 13:28:37 water kernel: [    0.124722] PCI: CLS 32 bytes, default 64
Jul  2 13:28:37 water kernel: [    0.124848] Simple Boot Flag at 0x35 set to 0x1
Jul  2 13:28:37 water kernel: [    0.125302] audit: initializing netlink socket (disabled)
Jul  2 13:28:37 water kernel: [    0.125324] type=2000 audit(1341250097.119:1): initialized
Jul  2 13:28:37 water kernel: [    0.155681] Trying to unpack rootfs image as initramfs...
Jul  2 13:28:37 water kernel: [    0.204439] highmem bounce pool size: 64 pages
Jul  2 13:28:37 water kernel: [    0.204450] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul  2 13:28:37 water kernel: [    0.236621] VFS: Disk quotas dquot_6.5.2
Jul  2 13:28:37 water kernel: [    0.236750] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul  2 13:28:37 water kernel: [    0.237992] fuse init (API version 7.16)
Jul  2 13:28:37 water kernel: [    0.238144] msgmni has been set to 1692
Jul  2 13:28:37 water kernel: [    0.252560] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul  2 13:28:37 water kernel: [    0.252604] io scheduler noop registered
Jul  2 13:28:37 water kernel: [    0.252607] io scheduler deadline registered
Jul  2 13:28:37 water kernel: [    0.252636] io scheduler cfq registered (default)
Jul  2 13:28:37 water kernel: [    0.252866] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  2 13:28:37 water kernel: [    0.252901] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul  2 13:28:37 water kernel: [    0.253185] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jul  2 13:28:37 water kernel: [    0.253360] ACPI: AC Adapter [AC] (on-line)
Jul  2 13:28:37 water kernel: [    0.253463] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Jul  2 13:28:37 water kernel: [    0.253616] ACPI: Lid Switch [LID]
Jul  2 13:28:37 water kernel: [    0.253680] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Jul  2 13:28:37 water kernel: [    0.253688] ACPI: Sleep Button [SLPB]
Jul  2 13:28:37 water kernel: [    0.253761] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jul  2 13:28:37 water kernel: [    0.253766] ACPI: Power Button [PWRF]
Jul  2 13:28:37 water kernel: [    0.253797] ACPI: acpi_idle registered with cpuidle
Jul  2 13:28:37 water kernel: [    0.254258] Marking TSC unstable due to TSC halts in idle
Jul  2 13:28:37 water kernel: [    0.264997] thermal LNXTHERM:00: registered as thermal_zone0
Jul  2 13:28:37 water kernel: [    0.265002] ACPI: Thermal Zone [THM0] (70 C)
Jul  2 13:28:37 water kernel: [    0.265057] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jul  2 13:28:37 water kernel: [    0.265092] ERST: Table is not found!
Jul  2 13:28:37 water kernel: [    0.265245] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul  2 13:28:37 water kernel: [    0.266985] serial 00:0a: [io  0x03f8-0x03ff]
Jul  2 13:28:37 water kernel: [    0.267044] serial 00:0a: [irq 4]
Jul  2 13:28:37 water kernel: [    0.267389] serial 00:0a: activated
Jul  2 13:28:37 water kernel: [    0.267524] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
Jul  2 13:28:37 water kernel: [    0.267670] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:28:37 water kernel: [    0.267679] serial 0000:00:1f.6: PCI INT B disabled
Jul  2 13:28:37 water kernel: [    0.267847] Linux agpgart interface v0.103
Jul  2 13:28:37 water kernel: [    0.267977] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
Jul  2 13:28:37 water kernel: [    0.285775] isapnp: Scanning for PnP cards...
Jul  2 13:28:37 water kernel: [    0.348718] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Jul  2 13:28:37 water kernel: [    0.441626] brd: module loaded
Jul  2 13:28:37 water kernel: [    0.442519] loop: module loaded
Jul  2 13:28:37 water kernel: [    0.442805] ata_piix 0000:00:1f.1: version 2.13
Jul  2 13:28:37 water kernel: [    0.442821] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
Jul  2 13:28:37 water kernel: [    0.443082] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Jul  2 13:28:37 water kernel: [    0.443089] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:28:37 water kernel: [    0.443154] ata_piix 0000:00:1f.1: setting latency timer to 64
Jul  2 13:28:37 water kernel: [    0.448072] scsi0 : ata_piix
Jul  2 13:28:37 water kernel: [    0.448300] scsi1 : ata_piix
Jul  2 13:28:37 water kernel: [    0.448991] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
Jul  2 13:28:37 water kernel: [    0.448995] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
Jul  2 13:28:37 water kernel: [    0.449603] Fixed MDIO Bus: probed
Jul  2 13:28:37 water kernel: [    0.449642] PPP generic driver version 2.4.2
Jul  2 13:28:37 water kernel: [    0.449757] tun: Universal TUN/TAP device driver, 1.6
Jul  2 13:28:37 water kernel: [    0.449760] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul  2 13:28:37 water kernel: [    0.449914] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul  2 13:28:37 water kernel: [    0.449940] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Jul  2 13:28:37 water kernel: [    0.449947] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Jul  2 13:28:37 water kernel: [    0.450158] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Jul  2 13:28:37 water kernel: [    0.450165] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:28:37 water kernel: [    0.450191] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jul  2 13:28:37 water kernel: [    0.450196] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul  2 13:28:37 water kernel: [    0.450246] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jul  2 13:28:37 water kernel: [    0.450289] ehci_hcd 0000:00:1d.7: debug port 1
Jul  2 13:28:37 water kernel: [    0.454168] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Jul  2 13:28:37 water kernel: [    0.456062] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
Jul  2 13:28:37 water kernel: [    0.468402] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jul  2 13:28:37 water kernel: [    0.468704] hub 1-0:1.0: USB hub found
Jul  2 13:28:37 water kernel: [    0.468712] hub 1-0:1.0: 6 ports detected
Jul  2 13:28:37 water kernel: [    0.468831] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul  2 13:28:37 water kernel: [    0.468859] uhci_hcd: USB Universal Host Controller Interface driver
Jul  2 13:28:37 water kernel: [    0.468949] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Jul  2 13:28:37 water kernel: [    0.468954] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Jul  2 13:28:37 water kernel: [    0.468969] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:28:37 water kernel: [    0.468983] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jul  2 13:28:37 water kernel: [    0.468988] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul  2 13:28:37 water kernel: [    0.469055] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jul  2 13:28:37 water kernel: [    0.469090] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
Jul  2 13:28:37 water kernel: [    0.469275] hub 2-0:1.0: USB hub found
Jul  2 13:28:37 water kernel: [    0.469281] hub 2-0:1.0: 2 ports detected
Jul  2 13:28:37 water kernel: [    0.469354] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Jul  2 13:28:37 water kernel: [    0.469359] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Jul  2 13:28:37 water kernel: [    0.469619] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Jul  2 13:28:37 water kernel: [    0.469625] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:28:37 water kernel: [    0.469632] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jul  2 13:28:37 water kernel: [    0.469637] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul  2 13:28:37 water kernel: [    0.469694] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jul  2 13:28:37 water kernel: [    0.469719] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
Jul  2 13:28:37 water kernel: [    0.469905] hub 3-0:1.0: USB hub found
Jul  2 13:28:37 water kernel: [    0.469910] hub 3-0:1.0: 2 ports detected
Jul  2 13:28:37 water kernel: [    0.469988] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:28:37 water kernel: [    0.469996] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jul  2 13:28:37 water kernel: [    0.470000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul  2 13:28:37 water kernel: [    0.470047] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jul  2 13:28:37 water kernel: [    0.470071] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
Jul  2 13:28:37 water kernel: [    0.470246] hub 4-0:1.0: USB hub found
Jul  2 13:28:37 water kernel: [    0.470251] hub 4-0:1.0: 2 ports detected
Jul  2 13:28:37 water kernel: [    0.470411] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Jul  2 13:28:37 water kernel: [    0.480777] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul  2 13:28:37 water kernel: [    0.480799] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul  2 13:28:37 water kernel: [    0.481038] mousedev: PS/2 mouse device common for all mice
Jul  2 13:28:37 water kernel: [    0.481760] rtc_cmos 00:06: RTC can wake from S4
Jul  2 13:28:37 water kernel: [    0.481889] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Jul  2 13:28:37 water kernel: [    0.481915] rtc0: alarms up to one month, y3k, 114 bytes nvram
Jul  2 13:28:37 water kernel: [    0.482137] device-mapper: uevent: version 1.0.3
Jul  2 13:28:37 water kernel: [    0.482813] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
Jul  2 13:28:37 water kernel: [    0.482875] EISA: Probing bus 0 at eisa.0
Jul  2 13:28:37 water kernel: [    0.482884] Cannot allocate resource for EISA slot 1
Jul  2 13:28:37 water kernel: [    0.482888] Cannot allocate resource for EISA slot 2
Jul  2 13:28:37 water kernel: [    0.482891] Cannot allocate resource for EISA slot 3
Jul  2 13:28:37 water kernel: [    0.482894] Cannot allocate resource for EISA slot 4
Jul  2 13:28:37 water kernel: [    0.482897] Cannot allocate resource for EISA slot 5
Jul  2 13:28:37 water kernel: [    0.482900] Cannot allocate resource for EISA slot 6
Jul  2 13:28:37 water kernel: [    0.482903] Cannot allocate resource for EISA slot 7
Jul  2 13:28:37 water kernel: [    0.482906] Cannot allocate resource for EISA slot 8
Jul  2 13:28:37 water kernel: [    0.482908] EISA: Detected 0 cards.
Jul  2 13:28:37 water kernel: [    0.482926] cpufreq-nforce2: No nForce2 chipset.
Jul  2 13:28:37 water kernel: [    0.482976] cpuidle: using governor ladder
Jul  2 13:28:37 water kernel: [    0.483049] cpuidle: using governor menu
Jul  2 13:28:37 water kernel: [    0.483052] EFI Variables Facility v0.08 2004-May-17
Jul  2 13:28:37 water kernel: [    0.484117] TCP cubic registered
Jul  2 13:28:37 water kernel: [    0.484366] NET: Registered protocol family 10
Jul  2 13:28:37 water kernel: [    0.485004] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul  2 13:28:37 water kernel: [    0.486118] NET: Registered protocol family 17
Jul  2 13:28:37 water kernel: [    0.486152] Registering the dns_resolver key type
Jul  2 13:28:37 water kernel: [    0.486194] Using IPI No-Shortcut mode
Jul  2 13:28:37 water kernel: [    0.486312] PM: Hibernation image not present or could not be loaded.
Jul  2 13:28:37 water kernel: [    0.486329] registered taskstats version 1
Jul  2 13:28:37 water kernel: [    0.676860] ata2.01: NODEV after polling detection
Jul  2 13:28:37 water kernel: [    0.677080] ata1.00: HPA detected: current 151144863, native 156301488
Jul  2 13:28:37 water kernel: [    0.677088] ata1.00: ATA-6: IC25N080ATMR04-0, MO4OADEA, max UDMA/100
Jul  2 13:28:37 water kernel: [    0.677092] ata1.00: 151144863 sectors, multi 16: LBA 
Jul  2 13:28:37 water kernel: [    0.684959] ata2.00: ATAPI: UJDA745 DVD/CDRW, 1.03, max UDMA/33
Jul  2 13:28:37 water kernel: [    0.688846] ata1.00: configured for UDMA/100
Jul  2 13:28:37 water kernel: [    0.700870] ata2.00: configured for UDMA/33
Jul  2 13:28:37 water kernel: [    0.799051] isapnp: No Plug & Play device found
Jul  2 13:28:37 water kernel: [    0.799497] scsi 0:0:0:0: Direct-Access     ATA      IC25N080ATMR04-0 MO4O PQ: 0 ANSI: 5
Jul  2 13:28:37 water kernel: [    0.799783] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul  2 13:28:37 water kernel: [    0.800051] sd 0:0:0:0: [sda] 151144863 512-byte logical blocks: (77.3 GB/72.0 GiB)
Jul  2 13:28:37 water kernel: [    0.800122] sd 0:0:0:0: [sda] Write Protect is off
Jul  2 13:28:37 water kernel: [    0.800126] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul  2 13:28:37 water kernel: [    0.800157] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  2 13:28:37 water kernel: [    0.803201] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA745 DVD/CDRW 1.03 PQ: 0 ANSI: 5
Jul  2 13:28:37 water kernel: [    0.807401] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jul  2 13:28:37 water kernel: [    0.807408] cdrom: Uniform CD-ROM driver Revision: 3.20
Jul  2 13:28:37 water kernel: [    0.807611] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jul  2 13:28:37 water kernel: [    0.807725] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul  2 13:28:37 water kernel: [    0.841540]  sda: sda1 sda2 < sda5 >
Jul  2 13:28:37 water kernel: [    0.841730] sda: p5 size 9762816 extends beyond EOD, enabling native capacity
Jul  2 13:28:37 water kernel: [    0.841811] ata1: soft resetting link
Jul  2 13:28:37 water kernel: [    0.851336] ACPI: Battery Slot [BAT0] (battery present)
Jul  2 13:28:37 water kernel: [    1.012497] ata1.00: n_sectors mismatch 151144863 != 156301488
Jul  2 13:28:37 water kernel: [    1.012503] ata1.00: new n_sectors matches native, probably late HPA unlock, n_sectors updated
Jul  2 13:28:37 water kernel: [    1.028904] ata1.00: configured for UDMA/100
Jul  2 13:28:37 water kernel: [    1.028917] ata1: EH complete
Jul  2 13:28:37 water kernel: [    1.029240] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Jul  2 13:28:37 water kernel: [    1.029439] sda: detected capacity change from 77386169856 to 80026361856
Jul  2 13:28:37 water kernel: [    1.060654] Freeing initrd memory: 13292k freed
Jul  2 13:28:37 water kernel: [    1.083345]  sda: sda1 sda2 < sda5 >
Jul  2 13:28:37 water kernel: [    1.087357] sd 0:0:0:0: [sda] Attached SCSI disk
Jul  2 13:28:37 water kernel: [    1.092111] usb 4-1: new full speed USB device number 2 using uhci_hcd
Jul  2 13:28:37 water kernel: [    1.092916]   Magic number: 4:883:490
Jul  2 13:28:37 water kernel: [    1.093106] rtc_cmos 00:06: setting system clock to 2012-07-02 17:28:18 UTC (1341250098)
Jul  2 13:28:37 water kernel: [    1.094139] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul  2 13:28:37 water kernel: [    1.094143] EDD information not available.
Jul  2 13:28:37 water kernel: [    1.094301] Freeing unused kernel memory: 696k freed
Jul  2 13:28:37 water kernel: [    1.094776] Write protecting the kernel text: 5332k
Jul  2 13:28:37 water kernel: [    1.094827] Write protecting the kernel read-only data: 2188k
Jul  2 13:28:37 water kernel: [    1.271895] Floppy drive(s): fd0 is 1.44M
Jul  2 13:28:37 water kernel: [    1.316920] FDC 0 is a National Semiconductor PC87306
Jul  2 13:28:37 water kernel: [    1.355164] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
Jul  2 13:28:37 water kernel: [    1.355170] e1000: Copyright (c) 1999-2006 Intel Corporation.
Jul  2 13:28:37 water kernel: [    1.355232] e1000 0000:02:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:28:37 water kernel: [    1.686520] e1000 0000:02:01.0: eth0: (PCI:33MHz:32-bit) 00:0d:60:10:85:f6
Jul  2 13:28:37 water kernel: [    1.686530] e1000 0000:02:01.0: eth0: Intel(R) PRO/1000 Network Connection
Jul  2 13:28:37 water kernel: [    1.868074] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jul  2 13:28:37 water kernel: [   19.286899] lp: driver loaded but no devices found
Jul  2 13:28:37 water kernel: [   19.316210] Adding 4881404k swap on /dev/sda5.  Priority:-1 extents:1 across:4881404k 
Jul  2 13:28:37 water kernel: [   19.410092] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul  2 13:28:37 water kernel: [   19.546784] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jul  2 13:28:37 water kernel: [   19.819564] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/LNXVIDEO:00/input/input4
Jul  2 13:28:37 water kernel: [   19.824118] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Jul  2 13:28:37 water kernel: [   19.892255] type=1400 audit(1341250117.298:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=511 comm="apparmor_parser"
Jul  2 13:28:37 water kernel: [   19.892930] type=1400 audit(1341250117.298:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=511 comm="apparmor_parser"
Jul  2 13:28:37 water kernel: [   19.893356] type=1400 audit(1341250117.298:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=511 comm="apparmor_parser"
Jul  2 13:28:37 water kernel: [   19.940176] parport_pc 00:0b: reported by Plug and Play ACPI
Jul  2 13:28:37 water kernel: [   19.940225] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
Jul  2 13:28:37 water kernel: [   19.948260] Non-volatile memory driver v1.3
Jul  2 13:28:37 water kernel: [   20.035901] lp0: using parport0 (interrupt-driven).
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin Wavecom
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin MotoC
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin Sierra
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin Generic
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin Option
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin Option High-Speed
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin Huawei
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin Longcheer
Jul  2 13:28:37 water NetworkManager[529]: <info> NetworkManager (version 0.9.1.90) is starting...
Jul  2 13:28:37 water NetworkManager[529]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin Samsung
Jul  2 13:28:37 water modem-manager[513]: <info>  Loaded plugin Linktop
Jul  2 13:28:37 water kernel: [   20.121909] irda_init()
Jul  2 13:28:37 water kernel: [   20.121932] NET: Registered protocol family 23
Jul  2 13:28:37 water kernel: [   20.174358] nsc-ircc 00:0c: [io  0x02f8-0x02ff]
Jul  2 13:28:37 water kernel: [   20.174423] nsc-ircc 00:0c: [irq 3]
Jul  2 13:28:37 water kernel: [   20.174429] nsc-ircc 00:0c: [dma 1]
Jul  2 13:28:37 water kernel: [   20.174892] nsc-ircc 00:0c: activated
Jul  2 13:28:37 water kernel: [   20.174898] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
Jul  2 13:28:37 water kernel: [   20.222714] nsc-ircc, chip->init
Jul  2 13:28:37 water kernel: [   20.222727] nsc-ircc, Found chip at base=0x02e
Jul  2 13:28:37 water kernel: [   20.222752] nsc-ircc, driver loaded (Dag Brattli)
Jul  2 13:28:37 water kernel: [   20.234464] IrDA: Registered device irda0
Jul  2 13:28:37 water kernel: [   20.234469] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
Jul  2 13:28:37 water kernel: [   20.235704] intel_rng: FWH not detected
Jul  2 13:28:37 water kernel: [   20.306611] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:0512]
Jul  2 13:28:37 water kernel: [   20.306631] yenta_cardbus 0000:02:00.0: Using INTVAL to route CSC interrupts to PCI
Jul  2 13:28:37 water kernel: [   20.306635] yenta_cardbus 0000:02:00.0: Routing CardBus interrupts to PCI
Jul  2 13:28:37 water kernel: [   20.306641] yenta_cardbus 0000:02:00.0: TI: mfunc 0x01d21022, devctl 0x64
Jul  2 13:28:37 water kernel: [   20.308495] Bluetooth: Core ver 2.16
Jul  2 13:28:37 water NetworkManager[529]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jul  2 13:28:37 water kernel: [   20.343725] NET: Registered protocol family 31
Jul  2 13:28:37 water kernel: [   20.343730] Bluetooth: HCI device and connection manager initialized
Jul  2 13:28:37 water kernel: [   20.343735] Bluetooth: HCI socket layer initialized
Jul  2 13:28:37 water kernel: [   20.343738] Bluetooth: L2CAP socket layer initialized
Jul  2 13:28:37 water kernel: [   20.344556] [drm] Initialized drm 1.1.0 20060810
Jul  2 13:28:37 water kernel: [   20.348881] Bluetooth: SCO socket layer initialized
Jul  2 13:28:37 water dbus[496]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jul  2 13:28:37 water kernel: [   20.434125] Bluetooth: Generic Bluetooth USB driver ver 0.6
Jul  2 13:28:37 water kernel: [   20.439724] usbcore: registered new interface driver btusb
Jul  2 13:28:37 water polkitd[544]: started daemon version 0.102 using authority implementation `local' version `0.102'
Jul  2 13:28:37 water dbus[496]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jul  2 13:28:37 water NetworkManager[529]:    SCPlugin-Ifupdown: init!
Jul  2 13:28:37 water NetworkManager[529]:    SCPlugin-Ifupdown: update_system_hostname
Jul  2 13:28:37 water NetworkManager[529]:    SCPluginIfupdown: management mode: unmanaged
Jul  2 13:28:37 water NetworkManager[529]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0)
Jul  2 13:28:37 water NetworkManager[529]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul  2 13:28:37 water NetworkManager[529]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/irda0, iface: irda0)
Jul  2 13:28:37 water NetworkManager[529]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/irda0, iface: irda0): no ifupdown configuration found.
Jul  2 13:28:37 water NetworkManager[529]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul  2 13:28:37 water NetworkManager[529]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul  2 13:28:37 water NetworkManager[529]:    SCPlugin-Ifupdown: end _init.
Jul  2 13:28:37 water NetworkManager[529]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul  2 13:28:37 water NetworkManager[529]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul  2 13:28:37 water NetworkManager[529]:    Ifupdown: get unmanaged devices count: 0
Jul  2 13:28:37 water NetworkManager[529]:    SCPlugin-Ifupdown: (152635536) ... get_connections.
Jul  2 13:28:37 water NetworkManager[529]:    SCPlugin-Ifupdown: (152635536) ... get_connections (managed=false): return empty list.
Jul  2 13:28:37 water NetworkManager[529]:    keyfile: parsing cabin ... 
Jul  2 13:28:37 water kernel: [   20.505121] cfg80211: Calling CRDA to update world regulatory domain
Jul  2 13:28:37 water NetworkManager[529]:    keyfile:     read connection 'cabin'
Jul  2 13:28:37 water kernel: [   20.536502] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x0438, PCI irq 11
Jul  2 13:28:37 water kernel: [   20.536509] yenta_cardbus 0000:02:00.0: Socket status: 30000006
Jul  2 13:28:37 water kernel: [   20.536530] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge window: [io  0x4000-0x8fff]
Jul  2 13:28:37 water NetworkManager[529]:    Ifupdown: get unmanaged devices count: 0
Jul  2 13:28:37 water NetworkManager[529]: <info> modem-manager is now available
Jul  2 13:28:37 water NetworkManager[529]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul  2 13:28:37 water NetworkManager[529]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul  2 13:28:37 water NetworkManager[529]: <info> WWAN enabled by radio killswitch; enabled by state file
Jul  2 13:28:37 water NetworkManager[529]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul  2 13:28:37 water NetworkManager[529]: <info> Networking is enabled by state file
Jul  2 13:28:37 water NetworkManager[529]: <info> (eth0): carrier is OFF
Jul  2 13:28:37 water NetworkManager[529]: <info> (eth0): new Ethernet device (driver: 'e1000' ifindex: 2)
Jul  2 13:28:37 water NetworkManager[529]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul  2 13:28:37 water NetworkManager[529]: <info> (eth0): now managed
Jul  2 13:28:37 water NetworkManager[529]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul  2 13:28:37 water NetworkManager[529]: <info> (eth0): bringing up device.
Jul  2 13:28:37 water NetworkManager[529]: <info> (eth0): preparing device.
Jul  2 13:28:37 water NetworkManager[529]: <info> (eth0): deactivating device (reason 'managed') [2]
Jul  2 13:28:37 water kernel: [   20.536535] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x8fff: excluding 0x4000-0x40ff 0x4400-0x44ff 0x4800-0x48ff 0x4c00-0x4cff
Jul  2 13:28:37 water kernel: [   20.588652] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  2 13:28:37 water NetworkManager[529]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0
Jul  2 13:28:38 water NetworkManager[529]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jul  2 13:28:38 water NetworkManager[529]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0)
Jul  2 13:28:38 water NetworkManager[529]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul  2 13:28:38 water kernel: [   20.745504] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:28:38 water kernel: [   20.745540] Intel ICH 0000:00:1f.5: setting latency timer to 64
Jul  2 13:28:38 water udev-configure-printer: add /module/lp
Jul  2 13:28:38 water udev-configure-printer: Failed to get parent
Jul  2 13:28:38 water kernel: [   20.795202]  0x8000-0x803f
Jul  2 13:28:38 water kernel: [   20.889677] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge window: [mem 0xc0200000-0xcfffffff]
Jul  2 13:28:38 water kernel: [   20.889685] pcmcia_socket pcmcia_socket0: cs: memory probe 0xc0200000-0xcfffffff: excluding 0xc0200000-0xc09fffff 0xc3a00000-0xcc1fffff 0xcfa00000-0xd01fffff
Jul  2 13:28:38 water kernel: [   20.889715] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge window: [mem 0xe8000000-0xefffffff pref]
Jul  2 13:28:38 water kernel: [   20.889719] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe8000000-0xefffffff: excluding 0xe8000000-0xefffffff
Jul  2 13:28:38 water kernel: [   20.909244] ath5k 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:28:38 water NetworkManager[529]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul  2 13:28:38 water NetworkManager[529]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul  2 13:28:38 water failsafe: Failsafe of 120 seconds reached.
Jul  2 13:28:39 water NetworkManager[529]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/irda0, iface: irda0)
Jul  2 13:28:39 water NetworkManager[529]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/irda0, iface: irda0): no ifupdown configuration found.
Jul  2 13:28:39 water acpid: starting up with proc fs
Jul  2 13:28:39 water acpid: 32 rules loaded
Jul  2 13:28:39 water acpid: waiting for events: event logging is off
Jul  2 13:28:39 water cron[769]: (CRON) INFO (pidfile fd = 3)
Jul  2 13:28:39 water anacron[786]: Anacron 2.3 started on 2012-07-02
Jul  2 13:28:39 water cron[787]: (CRON) STARTUP (fork ok)
Jul  2 13:28:39 water cron[787]: (CRON) INFO (Running @reboot jobs)
Jul  2 13:28:39 water kernel: [   20.909312] ath5k 0000:02:02.0: registered as 'phy0'
Jul  2 13:28:39 water kernel: [   21.266214] thinkpad_acpi: ThinkPad ACPI Extras v0.24
Jul  2 13:28:39 water kernel: [   21.266219] thinkpad_acpi: http://ibm-acpi.sf.net/
Jul  2 13:28:39 water kernel: [   21.266222] thinkpad_acpi: ThinkPad BIOS 1RETDMWW (3.18 ), EC 1RHT71WW-3.04
Jul  2 13:28:39 water kernel: [   21.266226] thinkpad_acpi: IBM ThinkPad T40 , model 237392U
Jul  2 13:28:39 water kernel: [   21.266229] thinkpad_acpi: WARNING: Outdated ThinkPad BIOS/EC firmware
Jul  2 13:28:39 water kernel: [   21.266232] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
Jul  2 13:28:39 water kernel: [   21.285511] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
Jul  2 13:28:39 water kernel: [   21.296185] ath: EEPROM regdomain: 0x61
Jul  2 13:28:39 water kernel: [   21.296190] ath: EEPROM indicates we should expect a direct regpair map
Jul  2 13:28:39 water kernel: [   21.296196] ath: Country alpha2 being used: 00
Jul  2 13:28:39 water kernel: [   21.296199] ath: Regpair used: 0x61
Jul  2 13:28:39 water kernel: [   21.296207] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0/0x0
Jul  2 13:28:39 water kernel: [   21.296216] serio: Synaptics pass-through port at isa0060/serio1/input0
Jul  2 13:28:39 water kernel: [   21.297445] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297451] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   21.297454] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297459] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   21.297462] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297466] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   21.297470] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297474] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   21.297478] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297482] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   21.297485] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297490] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   21.297493] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297497] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   21.297501] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297505] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   21.297508] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297513] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   21.297516] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297520] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   21.297524] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297528] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   21.297532] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297536] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   21.297539] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297544] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   21.297547] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297551] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   21.297555] cfg80211: Disabling freq 5040 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jul  2 13:28:39 water kernel: [   21.297559] cfg80211: Disabling freq 5060 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jul  2 13:28:39 water kernel: [   21.297563] cfg80211: Disabling freq 5080 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jul  2 13:28:39 water kernel: [   21.297566] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297571] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297574] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297578] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297582] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297586] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297590] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water anacron[786]: Will run job `cron.weekly' in 10 min.
Jul  2 13:28:39 water anacron[786]: Jobs will be executed sequentially
Jul  2 13:28:39 water kernel: [   21.297594] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297597] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297602] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297605] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297609] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297613] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297617] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297620] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297625] cfg80211: 5140000 KHz - 5360000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297628] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297632] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297636] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297640] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297644] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297648] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297651] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297656] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297659] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297663] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297667] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297671] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297675] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297679] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297682] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297687] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297690] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297694] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297698] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297702] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297705] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297710] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297713] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297718] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297721] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297725] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297729] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297733] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297736] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297741] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.297744] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
Jul  2 13:28:39 water kernel: [   21.297748] cfg80211: 5460000 KHz - 5860000 KHz @  KHz), (N/A mBi, 3000 mBm)
Jul  2 13:28:39 water kernel: [   21.331341] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Jul  2 13:28:39 water kernel: [   21.336763] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
Jul  2 13:28:39 water kernel: [   21.376115] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
Jul  2 13:28:39 water kernel: [   21.379586] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jul  2 13:28:39 water kernel: [   21.382782] Registered led device: tpacpi::thinklight
Jul  2 13:28:39 water kernel: [   21.382993] Registered led device: ath5k-phy0::rx
Jul  2 13:28:39 water kernel: [   21.384110] Registered led device: ath5k-phy0::tx
Jul  2 13:28:39 water kernel: [   21.384135] ath5k phy0: Atheros AR5211 chip found (MAC: 0x42, PHY: 0x30)
Jul  2 13:28:39 water kernel: [   21.384138] ath5k phy0: RF5111 5GHz radio found (0x17)
Jul  2 13:28:39 water kernel: [   21.384141] ath5k phy0: RF2111 2GHz radio found (0x23)
Jul  2 13:28:39 water kernel: [   21.384193] yenta_cardbus 0000:02:00.1: CardBus bridge found [1014:0512]
Jul  2 13:28:39 water kernel: [   21.384212] yenta_cardbus 0000:02:00.1: Using INTVAL to route CSC interrupts to PCI
Jul  2 13:28:39 water kernel: [   21.384216] yenta_cardbus 0000:02:00.1: Routing CardBus interrupts to PCI
Jul  2 13:28:39 water kernel: [   21.384222] yenta_cardbus 0000:02:00.1: TI: mfunc 0x01d21022, devctl 0x64
Jul  2 13:28:39 water kernel: [   21.399172] Registered led device: tpacpi::power
Jul  2 13:28:39 water kernel: [   21.399253] Registered led device: tpacpi::standby
Jul  2 13:28:39 water kernel: [   21.431970] type=1400 audit(1341250118.834:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=696 comm="apparmor_parser"
Jul  2 13:28:39 water kernel: [   21.437511] type=1400 audit(1341250118.842:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=699 comm="apparmor_parser"
Jul  2 13:28:39 water kernel: [   21.441563] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
Jul  2 13:28:39 water kernel: [   21.443707] type=1400 audit(1341250118.846:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=699 comm="apparmor_parser"
Jul  2 13:28:39 water kernel: [   21.444199] type=1400 audit(1341250118.850:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=699 comm="apparmor_parser"
Jul  2 13:28:39 water kernel: [   21.445512] [drm] radeon defaulting to kernel modesetting.
Jul  2 13:28:39 water kernel: [   21.445516] [drm] radeon kernel modesetting enabled.
Jul  2 13:28:39 water kernel: [   21.445647] radeon 0000:01:00.0: power state changed by ACPI to D0
Jul  2 13:28:39 water kernel: [   21.445654] radeon 0000:01:00.0: power state changed by ACPI to D0
Jul  2 13:28:39 water kernel: [   21.445667] radeon 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul  2 13:28:39 water kernel: [   21.480142] type=1400 audit(1341250118.886:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=700 comm="apparmor_parser"
Jul  2 13:28:39 water kernel: [   21.496689] [drm] initializing kernel modesetting (RV250 0x1002:0x4C66 0x1014:0x0531).
Jul  2 13:28:39 water kernel: [   21.496728] [drm] register mmio base: 0xC0100000
Jul  2 13:28:39 water kernel: [   21.496730] [drm] register mmio size: 65536
Jul  2 13:28:39 water kernel: [   21.497031] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
Jul  2 13:28:39 water kernel: [   21.497050] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
Jul  2 13:28:39 water kernel: [   21.497090] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
Jul  2 13:28:39 water kernel: [   21.497119] radeon 0000:01:00.0: GTT: 256M 0xD0000000 - 0xDFFFFFFF
Jul  2 13:28:39 water kernel: [   21.497130] radeon 0000:01:00.0: VRAM: 128M 0x00000000E0000000 - 0x00000000E7FFFFFF (32M used)
Jul  2 13:28:39 water kernel: [   21.497141] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jul  2 13:28:39 water kernel: [   21.497144] [drm] Driver supports precise vblank timestamp query.
Jul  2 13:28:39 water kernel: [   21.497169] [drm] radeon: irq initialized.
Jul  2 13:28:39 water kernel: [   21.497524] [drm] Detected VRAM RAM=128M, BAR=128M
Jul  2 13:28:39 water kernel: [   21.497530] [drm] RAM width 64bits DDR
Jul  2 13:28:39 water kernel: [   21.501881] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
Jul  2 13:28:39 water kernel: [   21.510965] type=1400 audit(1341250118.914:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=700 comm="apparmor_parser"
Jul  2 13:28:39 water kernel: [   21.522011] [TTM] Zone  kernel: Available graphics memory: 440360 kiB.
Jul  2 13:28:39 water kernel: [   21.522015] [TTM] Zone highmem: Available graphics memory: 771820 kiB.
Jul  2 13:28:39 water kernel: [   21.522019] [TTM] Initializing pool allocator.
Jul  2 13:28:39 water kernel: [   21.522059] [drm] radeon: 32M of VRAM memory ready
Jul  2 13:28:39 water kernel: [   21.522063] [drm] radeon: 256M of GTT memory ready.
Jul  2 13:28:39 water kernel: [   21.523254] radeon 0000:01:00.0: WB disabled
Jul  2 13:28:39 water kernel: [   21.525066] type=1400 audit(1341250118.930:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=700 comm="apparmor_parser"
Jul  2 13:28:39 water kernel: [   21.548525] [drm] Loading R200 Microcode
Jul  2 13:28:39 water kernel: [   21.618402] yenta_cardbus 0000:02:00.1: ISA IRQ mask 0x0438, PCI irq 11
Jul  2 13:28:39 water kernel: [   21.618409] yenta_cardbus 0000:02:00.1: Socket status: 30000006
Jul  2 13:28:39 water kernel: [   21.618421] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge window: [io  0x4000-0x8fff]
Jul  2 13:28:39 water kernel: [   21.618427] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x8fff: excluding 0x4000-0x40ff 0x4400-0x44ff 0x4800-0x48ff 0x4c00-0x4cff
Jul  2 13:28:39 water kernel: [   21.729973] ppdev: user-space parallel port driver
Jul  2 13:28:39 water kernel: [   21.879702] init: failsafe main process (633) killed by TERM signal
Jul  2 13:28:39 water kernel: [   21.893047] init: apport pre-start process (762) terminated with status 1
Jul  2 13:28:39 water kernel: [   21.971486] init: apport post-stop process (790) terminated with status 1
Jul  2 13:28:39 water kernel: [   21.972400] intel8x0_measure_ac97_clock: measured 63028 usecs (3035 samples)
Jul  2 13:28:39 water kernel: [   21.972404] intel8x0: clocking to 48000
Jul  2 13:28:39 water udev-configure-printer: add /devices/pnp0/00:0b/printer/lp0
Jul  2 13:28:39 water udev-configure-printer: Failed to get parent
Jul  2 13:28:39 water kernel: [   22.035649]  0x8000-0x803f
Jul  2 13:28:39 water kernel: [   22.130498] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge window: [mem 0xc0200000-0xcfffffff]
Jul  2 13:28:39 water kernel: [   22.130506] pcmcia_socket pcmcia_socket1: cs: memory probe 0xc0200000-0xcfffffff: excluding 0xc0200000-0xc09fffff 0xc3a00000-0xcc1fffff 0xcfa00000-0xd01fffff
Jul  2 13:28:39 water kernel: [   22.130536] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge window: [mem 0xe8000000-0xefffffff pref]
Jul  2 13:28:39 water kernel: [   22.130541] pcmcia_socket pcmcia_socket1: cs: memory probe 0xe8000000-0xefffffff: excluding 0xe8000000-0xefffffff
Jul  2 13:28:39 water NetworkManager[529]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/ieee80211/phy0/rfkill1) (driver (unknown))
Jul  2 13:28:39 water kernel: [   22.251161] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Jul  2 13:28:39 water kernel: [   22.251168] cfg80211: World regulatory domain updated:
Jul  2 13:28:39 water kernel: [   22.251171] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul  2 13:28:39 water kernel: [   22.251175] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   22.251179] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   22.251184] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   22.251188] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   22.251192] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 13:28:39 water kernel: [   22.318868] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377
Jul  2 13:28:39 water kernel: [   22.319911] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
Jul  2 13:28:39 water kernel: [   22.355619] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Jul  2 13:28:39 water bluetoothd[843]: Bluetooth daemon 4.96
Jul  2 13:28:39 water bluetoothd[843]: Starting SDP server
Jul  2 13:28:39 water kernel: [   22.376586] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Jul  2 13:28:39 water kernel: [   22.377052] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xdc000-0xfffff
Jul  2 13:28:39 water kernel: [   22.377123] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Jul  2 13:28:39 water kernel: [   22.377192] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x600fffff
Jul  2 13:28:39 water kernel: [   22.377269] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Jul  2 13:28:39 water kernel: [   22.378825] Bluetooth: RFCOMM TTY layer initialized
Jul  2 13:28:39 water kernel: [   22.378833] Bluetooth: RFCOMM socket layer initialized
Jul  2 13:28:39 water kernel: [   22.378835] Bluetooth: RFCOMM ver 1.11
Jul  2 13:28:39 water bluetoothd[843]: Listening for HCI events on hci0
Jul  2 13:28:39 water bluetoothd[843]: HCI dev 0 up
Jul  2 13:28:39 water NetworkManager[529]: <warn> bluez error getting default adapter: No such adapter
Jul  2 13:28:39 water kernel: [   22.384175] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul  2 13:28:39 water kernel: [   22.384181] Bluetooth: BNEP filters: protocol multicast
Jul  2 13:28:39 water bluetoothd[843]: Adapter /org/bluez/843/hci0 has been enabled
Jul  2 13:28:39 water kernel: [   22.430677] [drm] radeon: ring at 0x00000000D0001000
Jul  2 13:28:39 water bluetoothd[843]: Inquiry Cancel Failed with status 0x0c
Jul  2 13:28:39 water kernel: [   22.430702] [drm] ring test succeeded in 1 usecs
Jul  2 13:28:39 water kernel: [   22.431011] [drm] radeon: ib pool ready.
Jul  2 13:28:39 water kernel: [   22.431132] [drm] ib test succeeded in 0 usecs
Jul  2 13:28:39 water kernel: [   22.431759] [drm] Panel ID String: SXGA+ Single (85MHz)    
Jul  2 13:28:39 water kernel: [   22.431763] [drm] Panel Size 1400x1050
Jul  2 13:28:39 water kernel: [   22.442881] [drm] radeon legacy LVDS backlight initialized
Jul  2 13:28:39 water kernel: [   22.443282] [drm] No TV DAC info found in BIOS
Jul  2 13:28:39 water kernel: [   22.446066] [drm] Radeon Display Connectors
Jul  2 13:28:39 water kernel: [   22.446073] [drm] Connector 0:
Jul  2 13:28:39 water kernel: [   22.446076] [drm]   VGA
Jul  2 13:28:39 water kernel: [   22.446080] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
Jul  2 13:28:39 water kernel: [   22.446082] [drm]   Encoders:
Jul  2 13:28:39 water kernel: [   22.446085] [drm]     CRT1: INTERNAL_DAC1
Jul  2 13:28:39 water kernel: [   22.446087] [drm] Connector 1:
Jul  2 13:28:39 water kernel: [   22.446089] [drm]   DVI-D
Jul  2 13:28:39 water kernel: [   22.446091] [drm]   HPD1
Jul  2 13:28:39 water kernel: [   22.446095] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Jul  2 13:28:39 water kernel: [   22.446097] [drm]   Encoders:
Jul  2 13:28:39 water kernel: [   22.446099] [drm]     DFP1: INTERNAL_TMDS1
Jul  2 13:28:39 water kernel: [   22.446102] [drm] Connector 2:
Jul  2 13:28:39 water kernel: [   22.446104] [drm]   LVDS
Jul  2 13:28:39 water kernel: [   22.446106] [drm]   Encoders:
Jul  2 13:28:39 water kernel: [   22.446108] [drm]     LCD1: INTERNAL_LVDS
Jul  2 13:28:39 water kernel: [   22.446110] [drm] Connector 3:
Jul  2 13:28:39 water kernel: [   22.446112] [drm]   S-video
Jul  2 13:28:39 water kernel: [   22.446114] [drm]   Encoders:
Jul  2 13:28:39 water kernel: [   22.446116] [drm]     TV1: INTERNAL_DAC2
Jul  2 13:28:39 water kernel: [   22.530531] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377
Jul  2 13:28:39 water kernel: [   22.531622] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
Jul  2 13:28:39 water kernel: [   22.589235] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
Jul  2 13:28:39 water kernel: [   22.589630] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
Jul  2 13:28:40 water kernel: [   22.602270] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xdc000-0xfffff
Jul  2 13:28:40 water kernel: [   22.602360] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Jul  2 13:28:40 water kernel: [   22.602431] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x600fffff
Jul  2 13:28:40 water kernel: [   22.602511] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
Jul  2 13:28:40 water NetworkManager[529]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jul  2 13:28:40 water NetworkManager[529]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 4)
Jul  2 13:28:40 water NetworkManager[529]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul  2 13:28:40 water NetworkManager[529]: <info> (wlan0): now managed
Jul  2 13:28:40 water NetworkManager[529]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul  2 13:28:40 water NetworkManager[529]: <info> (wlan0): bringing up device.
Jul  2 13:28:40 water NetworkManager[529]: <info> (wlan0): preparing device.
Jul  2 13:28:40 water NetworkManager[529]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jul  2 13:28:40 water kernel: [   22.676521] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  2 13:28:40 water dbus[496]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jul  2 13:28:40 water NetworkManager[529]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wlan0, iface: wlan0)
Jul  2 13:28:40 water NetworkManager[529]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul  2 13:28:40 water dbus[496]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jul  2 13:28:40 water NetworkManager[529]: <info> wpa_supplicant started
Jul  2 13:28:40 water kernel: [   22.680777] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
Jul  2 13:28:40 water NetworkManager[529]: <info> (wlan0): supplicant interface state: starting -> ready
Jul  2 13:28:40 water NetworkManager[529]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul  2 13:28:40 water NetworkManager[529]: <info> (wlan0): supplicant interface state: ready -> inactive
Jul  2 13:28:40 water kernel: [   22.754385] [drm] Radeon display connector DVI-D-1: No monitor connected or invalid EDID
Jul  2 13:28:40 water kernel: [   22.754430] [drm] radeon: power management initialized
Jul  2 13:28:40 water kernel: [   22.810247] [drm] fb mappable at 0xE0040000
Jul  2 13:28:40 water kernel: [   22.810252] [drm] vram apper at 0xE0000000
Jul  2 13:28:40 water kernel: [   22.810254] [drm] size 1478656
Jul  2 13:28:40 water kernel: [   22.810256] [drm] fb depth is 8
Jul  2 13:28:40 water kernel: [   22.810259] [drm]    pitch is 1408
Jul  2 13:28:40 water kernel: [   22.810515] fbcon: radeondrmfb (fb0) is primary device
Jul  2 13:28:40 water kernel: [   22.811687] Console: switching to colour frame buffer device 175x65
Jul  2 13:28:40 water kernel: [   22.811761] fb0: radeondrmfb frame buffer device
Jul  2 13:28:40 water kernel: [   22.811764] drm: registered panic notifier
Jul  2 13:28:40 water kernel: [   22.811778] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:00.0 on minor 0
Jul  2 13:28:40 water acpid: client connected from 983[0:0]
Jul  2 13:28:40 water acpid: 1 client rule loaded
Jul  2 13:28:40 water udev-configure-printer: add /devices/pnp0/00:0b/printer/lp0
Jul  2 13:28:40 water udev-configure-printer: Failed to get parent
Jul  2 13:28:40 water udev-configure-printer: add /module/lp
Jul  2 13:28:40 water udev-configure-printer: Failed to get parent
Jul  2 13:28:41 water dbus[496]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jul  2 13:28:41 water dbus[496]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jul  2 13:28:41 water accounts-daemon[993]: started daemon version 0.6.14
Jul  2 13:28:41 water kernel: [   23.797868] psmouse serio2: ID: 10 00 64
Jul  2 13:28:41 water dbus[496]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jul  2 13:28:41 water dbus[496]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jul  2 13:28:42 water kernel: [   24.861045] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jul  2 13:28:42 water dbus[496]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jul  2 13:28:42 water dbus[496]: [system] Successfully activated service 'org.freedesktop.UPower'
Jul  2 13:28:42 water kernel: [   25.424817] init: plymouth-stop pre-start process (1180) terminated with status 1
Jul  2 13:28:43 water dbus[496]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jul  2 13:28:43 water dbus[496]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jul  2 13:28:44 water kernel: [   26.595036] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jul  2 13:28:44 water dbus[496]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jul  2 13:28:44 water dbus[496]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jul  2 17:28:44 water rtkit-daemon[1255]: Successfully called chroot.
Jul  2 17:28:44 water rtkit-daemon[1255]: Successfully dropped privileges.
Jul  2 17:28:44 water rtkit-daemon[1255]: Successfully limited resources.
Jul  2 17:28:44 water rtkit-daemon[1255]: Running.
Jul  2 17:28:44 water rtkit-daemon[1255]: Watchdog thread running.
Jul  2 17:28:44 water rtkit-daemon[1255]: Canary thread running.
Jul  2 17:28:44 water rtkit-daemon[1255]: Successfully made thread 1253 of process 1253 (n/a) owned by '104' high priority at nice level -11.
Jul  2 17:28:44 water rtkit-daemon[1255]: Supervising 1 threads of 1 processes of 1 users.
Jul  2 13:28:44 water kernel: [   27.152754] IBM TrackPoint firmware: 0x0e, buttons: 3/3
Jul  2 17:28:44 water rtkit-daemon[1255]: Successfully made thread 1260 of process 1253 (n/a) owned by '104' RT at priority 5.
Jul  2 17:28:44 water rtkit-daemon[1255]: Supervising 2 threads of 1 processes of 1 users.
Jul  2 17:28:44 water rtkit-daemon[1255]: Successfully made thread 1261 of process 1253 (n/a) owned by '104' RT at priority 5.
Jul  2 17:28:44 water rtkit-daemon[1255]: Supervising 3 threads of 1 processes of 1 users.
Jul  2 13:28:44 water pulseaudio[1253]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Jul  2 13:28:44 water pulseaudio[1253]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Jul  2 13:28:44 water pulseaudio[1253]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Jul  2 13:28:44  pulseaudio[1253]: last message repeated 2 times
Jul  2 13:28:44 water kernel: [   27.378145] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input7
Jul  2 13:38:39 water anacron[786]: Job `cron.weekly' started
Jul  2 13:38:39 water anacron[1277]: Updated timestamp for job `cron.weekly' to 2012-07-02
Jul  2 13:41:20 water anacron[786]: Job `cron.weekly' terminated
Jul  2 13:41:20 water anacron[786]: Normal exit (1 job run)
Jul  2 14:17:01 water CRON[1310]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 15:17:01 water CRON[1323]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 15:24:01 water kernel: [ 6944.378818] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Jul  2 15:24:03 water anacron[1463]: Anacron 2.3 started on 2012-07-02
Jul  2 15:24:03 water anacron[1463]: Normal exit (0 jobs run)
Jul  2 15:24:04 water kernel: [ 6946.945951] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jul  2 15:24:10 water gnome-session[1508]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1
Jul  2 19:24:11 water rtkit-daemon[1255]: Successfully made thread 1593 of process 1593 (n/a) owned by '1000' high priority at nice level -11.
Jul  2 19:24:11 water rtkit-daemon[1255]: Supervising 4 threads of 2 processes of 2 users.
Jul  2 19:24:12 water rtkit-daemon[1255]: Successfully made thread 1596 of process 1593 (n/a) owned by '1000' RT at priority 5.
Jul  2 19:24:12 water rtkit-daemon[1255]: Supervising 5 threads of 2 processes of 2 users.
Jul  2 19:24:12 water rtkit-daemon[1255]: Successfully made thread 1597 of process 1593 (n/a) owned by '1000' RT at priority 5.
Jul  2 19:24:12 water rtkit-daemon[1255]: Supervising 6 threads of 2 processes of 2 users.
Jul  2 15:24:12 water pulseaudio[1593]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Jul  2 15:24:12 water pulseaudio[1593]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Jul  2 15:24:12 water pulseaudio[1593]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Jul  2 15:24:13  pulseaudio[1593]: last message repeated 2 times
Jul  2 15:24:13 water dbus[496]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jul  2 15:24:13 water dbus[496]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jul  2 15:24:16 water kernel: [ 6959.368109] usb 1-4: new high speed USB device number 3 using ehci_hcd
Jul  2 15:24:17 water mtp-probe: checking bus 1, device 3: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4"
Jul  2 15:24:17 water mtp-probe: bus: 1, device: 3 was not an MTP device
Jul  2 15:24:17 water kernel: [ 6959.755241] usbcore: registered new interface driver uas
Jul  2 15:24:17 water kernel: [ 6959.764811] Initializing USB Mass Storage driver...
Jul  2 15:24:17 water kernel: [ 6959.768366] scsi2 : usb-storage 1-4:1.0
Jul  2 15:24:17 water kernel: [ 6959.769259] usbcore: registered new interface driver usb-storage
Jul  2 15:24:17 water kernel: [ 6959.769265] USB Mass Storage support registered.
Jul  2 15:24:18 water kernel: [ 6960.777291] scsi 2:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2
Jul  2 15:24:18 water kernel: [ 6960.781310] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jul  2 15:24:18 water kernel: [ 6960.781379] sd 2:0:0:0: [sdb] 15794175 512-byte logical blocks: (8.08 GB/7.53 GiB)
Jul  2 15:24:18 water kernel: [ 6960.782377] sd 2:0:0:0: [sdb] Write Protect is off
Jul  2 15:24:18 water kernel: [ 6960.782383] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
Jul  2 15:24:18 water kernel: [ 6960.783381] sd 2:0:0:0: [sdb] Asking for cache data failed
Jul  2 15:24:18 water kernel: [ 6960.783387] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Jul  2 15:24:18 water kernel: [ 6960.787885] sd 2:0:0:0: [sdb] Asking for cache data failed
Jul  2 15:24:18 water kernel: [ 6960.787894] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Jul  2 15:24:18 water kernel: [ 6960.904600]  sdb: sdb1
Jul  2 15:24:18 water kernel: [ 6960.910232] sd 2:0:0:0: [sdb] Asking for cache data failed
Jul  2 15:24:18 water kernel: [ 6960.910239] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Jul  2 15:24:18 water kernel: [ 6960.910245] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Jul  2 15:25:15 water dbus[496]: [system] Activating service name='org.debian.apt' (using servicehelper)
Jul  2 15:25:17 water AptDaemon: INFO: Initializing daemon
Jul  2 15:25:17 water dbus[496]: [system] Successfully activated service 'org.debian.apt'
Jul  2 15:25:17 water AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Jul  2 15:25:17 water AptDaemon.Trans: INFO: Simulate was called
Jul  2 15:25:17 water AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/f681d2f23d7c46bf90c53ec922598a1f
Jul  2 15:25:18 water dbus[496]: [system] Activating service name='com.ubuntu.SystemService' (using servicehelper)
Jul  2 15:25:19 water dbus[496]: [system] Successfully activated service 'com.ubuntu.SystemService'
Jul  2 15:25:22 water AptDaemon.Worker: INFO: Upgrade system with safe mode: 1

```

---

