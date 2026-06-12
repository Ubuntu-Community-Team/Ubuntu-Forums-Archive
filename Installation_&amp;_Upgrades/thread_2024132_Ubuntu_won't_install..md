---
title: "Ubuntu won't install."
date: 2012-07-13
forum: Installation &amp; Upgrades
---

### Post by gaiusross on 2012-07-13
Hi i'm having problems installing ubuntu. I've installed it on an old laptop with an amd atherlon 64 with 1GB Ram. This works fine.

What I'm having trouble with is installing ubuntu on a Biostar IDEQ 200N It has an Atherlon 3000+ with 1GB Ram and onboard graphics.
the below image shows the error.
[http://a7.sphotos.ak.fbcdn.net/hphotos-ak-snc7/288232_4265076546119_1409752951_o.jpg]("http://a7.sphotos.ak.fbcdn.net/hphotos-ak-snc7/288232_4265076546119_1409752951_o.jpg")

I have tried installing with udate selcted and with nothing selected. I did have 2x1GB sticks but here were errors when I tested them using Ubuntu. I tested them seperatly and found that one did not have any errors. I tested this stick 3 or 4 times to make sure and it passed 100% each time.

I have changed the HDD

I have tried installing from a dvd and a usb stick using the instructions from your website.

Ive increased the ram for the onboard gpu and even tried disabling bios shadowing of the video ram.

I can't think of what else to do apart from put in an agp gpu.

Has any one got any ideas what so ever?

Below is the spec of the PC.

[http://www.biostar.com.tw/app/en/sffpc/content.php?S_ID=3](http://www.biostar.com.tw/app/en/sffpc/content.php?S_ID=3)

Any help would be much appreciated. Thanks.

---

### Post by dino99 on 2012-07-13
here is how i do installation:

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

maybe you need to add option on the boot line, like nomodeset or noacpi (google about : "ubuntu boot option")

---

### Post by hovrashko on 2012-07-13
have you tried lighter edition like xUbuntu?

---

### Post by Cheesehead on 2012-07-13
Click OK, and enter the desktop session.

Look in /var/log for the syslog and/or installer log. Post them here, especially the last 10 lines or so.

---

### Post by gaiusross on 2012-08-17
Hi, thanks for all the help. I tried partitioning the HDD but it didn't seem to work. It kept on saying it needed a boot folder or something like that. I can't remember. I have just tried Xubuntu. Same problem. 

Here is the SYSLOG data:
Aug 17 15:10:33 xubuntu kernel: imklog 5.8.6, log source = /proc/kmsg started.
Aug 17 15:10:33 xubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1286" x-info="http://www.rsyslog.com"] start
Aug 17 15:10:33 xubuntu rsyslogd: rsyslogd's groupid changed to 103
Aug 17 15:10:33 xubuntu rsyslogd: rsyslogd's userid changed to 101
Aug 17 15:10:33 xubuntu rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Linux version 3.2.0-23-generic (buildd@palmer) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 (Ubuntu 3.2.0-23.36-generic 3.2.14)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] KERNEL supported cpus:
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   Intel GenuineIntel
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   AMD AuthenticAMD
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   NSC Geode by NSC
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   Centaur CentaurHauls
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Aug 17 15:10:33 xubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 17 15:10:33 xubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Aug 17 15:10:33 xubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Aug 17 15:10:33 xubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 17 15:10:33 xubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003dff0000 (usable)
Aug 17 15:10:33 xubuntu kernel: [    0.000000]  BIOS-e820: 000000003dff0000 - 000000003dff3000 (ACPI NVS)
Aug 17 15:10:33 xubuntu kernel: [    0.000000]  BIOS-e820: 000000003dff3000 - 000000003e000000 (ACPI data)
Aug 17 15:10:33 xubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Aug 17 15:10:33 xubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 17 15:10:33 xubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
Aug 17 15:10:33 xubuntu kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Aug 17 15:10:33 xubuntu kernel: [    0.000000] DMI 2.2 present.
Aug 17 15:10:33 xubuntu kernel: [    0.000000] DMI:    /nVidia-nForce, BIOS 6.00 PG 01/31/2005
Aug 17 15:10:33 xubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] last_pfn = 0x3dff0 max_arch_pfn = 0x100000
Aug 17 15:10:33 xubuntu kernel: [    0.000000] MTRR default type: uncachable
Aug 17 15:10:33 xubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   00000-9FFFF write-back
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   C0000-C7FFF write-protect
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   C8000-FFFFF uncachable
Aug 17 15:10:33 xubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   1 base 03E000000 mask FFE000000 uncachable
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   2 base 0E0000000 mask FFC000000 write-combining
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   3 disabled
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   4 disabled
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   5 disabled
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   6 disabled
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   7 disabled
Aug 17 15:10:33 xubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug 17 15:10:33 xubuntu kernel: [    0.000000] initial memory mapped : 0 - 01c00000
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Aug 17 15:10:33 xubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Aug 17 15:10:33 xubuntu kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Aug 17 15:10:33 xubuntu kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Aug 17 15:10:33 xubuntu kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Aug 17 15:10:33 xubuntu kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
Aug 17 15:10:33 xubuntu kernel: [    0.000000] RAMDISK: 3d11d000 - 3dfef000
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Allocated new RAMDISK: 3692c000 - 377fd0e6
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Move RAMDISK from 000000003d11d000 - 000000003dfee0e5 to 3692c000 - 377fd0e5
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: RSDP 000f7450 00014 (v00 Nvidia)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: RSDT 3dff3000 0002C (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: FACP 3dff3040 00074 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: DSDT 3dff30c0 048E9 (v01 NVIDIA AWRDACPI 00001000 MSFT 01000009)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: FACS 3dff0000 00040
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: APIC 3dff79c0 0005A (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 17 15:10:33 xubuntu kernel: [    0.000000] 103MB HIGHMEM available.
Aug 17 15:10:33 xubuntu kernel: [    0.000000] 887MB LOWMEM available.
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Zone PFN ranges:
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003dff0
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Movable zone start PFN for each node
Aug 17 15:10:33 xubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Aug 17 15:10:33 xubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Aug 17 15:10:33 xubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0003dff0
Aug 17 15:10:33 xubuntu kernel: [    0.000000] On node 0 totalpages: 253823
Aug 17 15:10:33 xubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c18258c0, node_mem_map f616b200
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   HighMem zone: 208 pages used for memmap
Aug 17 15:10:33 xubuntu kernel: [    0.000000]   HighMem zone: 26402 pages, LIFO batch:7
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Using APIC driver default
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Aug 17 15:10:33 xubuntu kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 17 15:10:33 xubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 17 15:10:33 xubuntu kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Aug 17 15:10:33 xubuntu kernel: [    0.000000] nr_irqs_gsi: 40
Aug 17 15:10:33 xubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 17 15:10:33 xubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Aug 17 15:10:33 xubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Allocating PCI resources starting at 3e000000 (gap: 3e000000:c0c00000)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug 17 15:10:33 xubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Aug 17 15:10:33 xubuntu kernel: [    0.000000] PERCPU: Embedded 13 pages/cpu @f5c00000 s31616 r0 d21632 u4194304
Aug 17 15:10:33 xubuntu kernel: [    0.000000] pcpu-alloc: s31616 r0 d21632 u4194304 alloc=1*4194304
Aug 17 15:10:33 xubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 251839
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Kernel command line: cdrom-detect/try-usb=true file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash -- BOOT_IMAGE=/casper/vmlinuz 
Aug 17 15:10:33 xubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Initializing CPU#0
Aug 17 15:10:33 xubuntu kernel: [    0.000000] allocated 4062720 bytes of page_cgroup
Aug 17 15:10:33 xubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003dff0)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Memory: 977304k/1015744k available (5627k kernel code, 37988k reserved, 2764k data, 712k init, 106440k highmem)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] virtual kernel memory layout:
Aug 17 15:10:33 xubuntu kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Aug 17 15:10:33 xubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 17 15:10:33 xubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Aug 17 15:10:33 xubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Aug 17 15:10:33 xubuntu kernel: [    0.000000]       .init : 0xc1833000 - 0xc18e5000   ( 712 kB)
Aug 17 15:10:33 xubuntu kernel: [    0.000000]       .data : 0xc157ef84 - 0xc1832080   (2764 kB)
Aug 17 15:10:33 xubuntu kernel: [    0.000000]       .text : 0xc1000000 - 0xc157ef84   (5627 kB)
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Aug 17 15:10:33 xubuntu kernel: [    0.000000] SLUB: Genslabs=15, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Aug 17 15:10:33 xubuntu kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Aug 17 15:10:33 xubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256 16
Aug 17 15:10:33 xubuntu kernel: [    0.000000] CPU 0 irqstacks, hard=f5808000 soft=f580a000
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Aug 17 15:10:33 xubuntu kernel: [    0.000000] console [tty0] enabled
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Aug 17 15:10:33 xubuntu kernel: [    0.000000] Detected 2162.770 MHz processor.
Aug 17 15:10:33 xubuntu kernel: [    0.008004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4325.54 BogoMIPS (lpj=8651080)
Aug 17 15:10:33 xubuntu kernel: [    0.008011] pid_max: default: 32768 minimum: 301
Aug 17 15:10:33 xubuntu kernel: [    0.008051] Security Framework initialized
Aug 17 15:10:33 xubuntu kernel: [    0.008092] AppArmor: AppArmor initialized
Aug 17 15:10:33 xubuntu kernel: [    0.008095] Yama: becoming mindful.
Aug 17 15:10:33 xubuntu kernel: [    0.008188] Mount-cache hash table entries: 512
Aug 17 15:10:33 xubuntu kernel: [    0.008419] Initializing cgroup subsys cpuacct
Aug 17 15:10:33 xubuntu kernel: [    0.008428] Initializing cgroup subsys memory
Aug 17 15:10:33 xubuntu kernel: [    0.008442] Initializing cgroup subsys devices
Aug 17 15:10:33 xubuntu kernel: [    0.008446] Initializing cgroup subsys freezer
Aug 17 15:10:33 xubuntu kernel: [    0.008450] Initializing cgroup subsys blkio
Aug 17 15:10:33 xubuntu kernel: [    0.008461] Initializing cgroup subsys perf_event
Aug 17 15:10:33 xubuntu kernel: [    0.008499] mce: CPU supports 4 MCE banks
Aug 17 15:10:33 xubuntu kernel: [    0.008575] SMP alternatives: switching to UP code
Aug 17 15:10:33 xubuntu kernel: [    0.019482] Freeing SMP alternatives: 24k freed
Aug 17 15:10:33 xubuntu kernel: [    0.019514] ACPI: Core revision 20110623
Aug 17 15:10:33 xubuntu kernel: [    0.025376] ftrace: allocating 25954 entries in 51 pages
Aug 17 15:10:33 xubuntu kernel: [    0.028154] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 17 15:10:33 xubuntu kernel: [    0.028613] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
Aug 17 15:10:33 xubuntu kernel: [    0.070308] CPU0: AMD Athlon(tm) XP 3000+ stepping 00
Aug 17 15:10:33 xubuntu kernel: [    0.072003] Performance Events: AMD PMU driver.
Aug 17 15:10:33 xubuntu kernel: [    0.072003] ... version:                0
Aug 17 15:10:33 xubuntu kernel: [    0.072003] ... bit width:              48
Aug 17 15:10:33 xubuntu kernel: [    0.072003] ... generic registers:      4
Aug 17 15:10:33 xubuntu kernel: [    0.072003] ... value mask:             0000ffffffffffff
Aug 17 15:10:33 xubuntu kernel: [    0.072003] ... max period:             00007fffffffffff
Aug 17 15:10:33 xubuntu kernel: [    0.072003] ... fixed-purpose events:   0
Aug 17 15:10:33 xubuntu kernel: [    0.072003] ... event mask:             000000000000000f
Aug 17 15:10:33 xubuntu kernel: [    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
Aug 17 15:10:33 xubuntu kernel: [    0.072003] Brought up 1 CPUs
Aug 17 15:10:33 xubuntu kernel: [    0.072003] Total of 1 processors activated (4325.54 BogoMIPS).
Aug 17 15:10:33 xubuntu kernel: [    0.072003] devtmpfs: initialized
Aug 17 15:10:33 xubuntu kernel: [    0.072003] EVM: security.selinux
Aug 17 15:10:33 xubuntu kernel: [    0.072003] EVM: security.SMACK64
Aug 17 15:10:33 xubuntu kernel: [    0.072003] EVM: security.capability
Aug 17 15:10:33 xubuntu kernel: [    0.072003] PM: Registering ACPI NVS region at 3dff0000 (12288 bytes)
Aug 17 15:10:33 xubuntu kernel: [    0.072003] print_constraints: dummy: 
Aug 17 15:10:33 xubuntu kernel: [    0.072003] RTC time: 15:10:10, date: 08/17/12
Aug 17 15:10:33 xubuntu kernel: [    0.072003] NET: Registered protocol family 16
Aug 17 15:10:33 xubuntu kernel: [    0.072003] EISA bus registered
Aug 17 15:10:33 xubuntu kernel: [    0.072003] ACPI: bus type pci registered
Aug 17 15:10:33 xubuntu kernel: [    0.103156] PCI: PCI BIOS revision 2.10 entry at 0xfb610, last bus=2
Aug 17 15:10:33 xubuntu kernel: [    0.103159] PCI: Using configuration type 1 for base access
Aug 17 15:10:33 xubuntu kernel: [    0.104934] bio: create slab <bio-0> at 0
Aug 17 15:10:33 xubuntu kernel: [    0.105065] ACPI: Added _OSI(Module Device)
Aug 17 15:10:33 xubuntu kernel: [    0.105068] ACPI: Added _OSI(Processor Device)
Aug 17 15:10:33 xubuntu kernel: [    0.105071] ACPI: Added _OSI(3.0 _SCP Extensions)
Aug 17 15:10:33 xubuntu kernel: [    0.105073] ACPI: Added _OSI(Processor Aggregator Device)
Aug 17 15:10:33 xubuntu kernel: [    0.106113] ACPI: EC: Look up EC in DSDT
Aug 17 15:10:33 xubuntu kernel: [    0.110064] ACPI: Interpreter enabled
Aug 17 15:10:33 xubuntu kernel: [    0.110071] ACPI: (supports S0 S1 S4 S5)
Aug 17 15:10:33 xubuntu kernel: [    0.110095] ACPI: Using IOAPIC for interrupt routing
Aug 17 15:10:33 xubuntu kernel: [    0.110776] ACPI: Power Resource [ISAV] (on)
Aug 17 15:10:33 xubuntu kernel: [    0.116675] ACPI: No dock devices found.
Aug 17 15:10:33 xubuntu kernel: [    0.116678] HEST: Table not found.
Aug 17 15:10:33 xubuntu kernel: [    0.116683] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Aug 17 15:10:33 xubuntu kernel: [    0.116759] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Aug 17 15:10:33 xubuntu kernel: [    0.116912] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cef] (ignored)
Aug 17 15:10:33 xubuntu kernel: [    0.116916] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Aug 17 15:10:33 xubuntu kernel: [    0.116920] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Aug 17 15:10:33 xubuntu kernel: [    0.116923] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
Aug 17 15:10:33 xubuntu kernel: [    0.116926] pci_root PNP0A03:00: host bridge window [mem 0x3e000000-0xfebfffff] (ignored)
Aug 17 15:10:33 xubuntu kernel: [    0.116944] pci 0000:00:00.0: [10de:01e0] type 0 class 0x000600
Aug 17 15:10:33 xubuntu kernel: [    0.116953] pci 0000:00:00.0: reg 10: [mem 0xe0000000-0xe3ffffff pref]
Aug 17 15:10:33 xubuntu kernel: [    0.116972] pci 0000:00:00.0: nForce2 C1 Halt Disconnect fixup
Aug 17 15:10:33 xubuntu kernel: [    0.117003] pci 0000:00:00.1: [10de:01eb] type 0 class 0x000500
Aug 17 15:10:33 xubuntu kernel: [    0.117041] pci 0000:00:00.2: [10de:01ee] type 0 class 0x000500
Aug 17 15:10:33 xubuntu kernel: [    0.117078] pci 0000:00:00.3: [10de:01ed] type 0 class 0x000500
Aug 17 15:10:33 xubuntu kernel: [    0.117113] pci 0000:00:00.4: [10de:01ec] type 0 class 0x000500
Aug 17 15:10:33 xubuntu kernel: [    0.117154] pci 0000:00:00.5: [10de:01ef] type 0 class 0x000500
Aug 17 15:10:33 xubuntu kernel: [    0.117197] pci 0000:00:01.0: [10de:0060] type 0 class 0x000601
Aug 17 15:10:33 xubuntu kernel: [    0.117284] pci 0000:00:01.1: [10de:0064] type 0 class 0x000c05
Aug 17 15:10:33 xubuntu kernel: [    0.117299] pci 0000:00:01.1: reg 10: [io  0xe400-0xe41f]
Aug 17 15:10:33 xubuntu kernel: [    0.117359] pci 0000:00:01.1: PME# supported from D3hot D3cold
Aug 17 15:10:33 xubuntu kernel: [    0.117364] pci 0000:00:01.1: PME# disabled
Aug 17 15:10:33 xubuntu kernel: [    0.117385] pci 0000:00:02.0: [10de:0067] type 0 class 0x000c03
Aug 17 15:10:33 xubuntu kernel: [    0.117775] pci 0000:00:02.0: reg 10: [mem 0xef080000-0xef080fff]
Aug 17 15:10:33 xubuntu kernel: [    0.117834] pci 0000:00:02.0: supports D1 D2
Aug 17 15:10:33 xubuntu kernel: [    0.117836] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 17 15:10:33 xubuntu kernel: [    0.117841] pci 0000:00:02.0: PME# disabled
Aug 17 15:10:33 xubuntu kernel: [    0.117858] pci 0000:00:02.1: [10de:0067] type 0 class 0x000c03
Aug 17 15:10:33 xubuntu kernel: [    0.117872] pci 0000:00:02.1: reg 10: [mem 0xef083000-0xef083fff]
Aug 17 15:10:33 xubuntu kernel: [    0.117931] pci 0000:00:02.1: supports D1 D2
Aug 17 15:10:33 xubuntu kernel: [    0.117933] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Aug 17 15:10:33 xubuntu kernel: [    0.117938] pci 0000:00:02.1: PME# disabled
Aug 17 15:10:33 xubuntu kernel: [    0.117956] pci 0000:00:02.2: [10de:0068] type 0 class 0x000c03
Aug 17 15:10:33 xubuntu kernel: [    0.117973] pci 0000:00:02.2: reg 10: [mem 0xef086000-0xef0860ff]
Aug 17 15:10:33 xubuntu kernel: [    0.118042] pci 0000:00:02.2: supports D1 D2
Aug 17 15:10:33 xubuntu kernel: [    0.118044] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
Aug 17 15:10:33 xubuntu kernel: [    0.118049] pci 0000:00:02.2: PME# disabled
Aug 17 15:10:33 xubuntu kernel: [    0.118074] pci 0000:00:04.0: [10de:0066] type 0 class 0x000200
Aug 17 15:10:33 xubuntu kernel: [    0.118089] pci 0000:00:04.0: reg 10: [mem 0xef087000-0xef087fff]
Aug 17 15:10:33 xubuntu kernel: [    0.118098] pci 0000:00:04.0: reg 14: [io  0xd000-0xd007]
Aug 17 15:10:33 xubuntu kernel: [    0.118150] pci 0000:00:04.0: supports D1 D2
Aug 17 15:10:33 xubuntu kernel: [    0.118153] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 17 15:10:33 xubuntu kernel: [    0.118157] pci 0000:00:04.0: PME# disabled
Aug 17 15:10:33 xubuntu kernel: [    0.118175] pci 0000:00:05.0: [10de:006b] type 0 class 0x000401
Aug 17 15:10:33 xubuntu kernel: [    0.118189] pci 0000:00:05.0: reg 10: [mem 0xef000000-0xef07ffff]
Aug 17 15:10:33 xubuntu kernel: [    0.118248] pci 0000:00:05.0: supports D1 D2
Aug 17 15:10:33 xubuntu kernel: [    0.118266] pci 0000:00:06.0: [10de:006a] type 0 class 0x000401
Aug 17 15:10:33 xubuntu kernel: [    0.118281] pci 0000:00:06.0: reg 10: [io  0xd400-0xd4ff]
Aug 17 15:10:33 xubuntu kernel: [    0.118290] pci 0000:00:06.0: reg 14: [io  0xd800-0xd87f]
Aug 17 15:10:33 xubuntu kernel: [    0.118299] pci 0000:00:06.0: reg 18: [mem 0xef081000-0xef081fff]
Aug 17 15:10:33 xubuntu kernel: [    0.118345] pci 0000:00:06.0: supports D1 D2
Aug 17 15:10:33 xubuntu kernel: [    0.118361] pci 0000:00:08.0: [10de:006c] type 1 class 0x000604
Aug 17 15:10:33 xubuntu kernel: [    0.118401] pci 0000:00:09.0: [10de:0065] type 0 class 0x000101
Aug 17 15:10:33 xubuntu kernel: [    0.118439] pci 0000:00:09.0: reg 20: [io  0xf000-0xf00f]
Aug 17 15:10:33 xubuntu kernel: [    0.118492] pci 0000:00:0d.0: [10de:006e] type 0 class 0x000c00
Aug 17 15:10:33 xubuntu kernel: [    0.118507] pci 0000:00:0d.0: reg 10: [mem 0xef084000-0xef0847ff]
Aug 17 15:10:33 xubuntu kernel: [    0.118516] pci 0000:00:0d.0: reg 14: [mem 0xef085000-0xef08503f]
Aug 17 15:10:33 xubuntu kernel: [    0.118568] pci 0000:00:0d.0: supports D1 D2
Aug 17 15:10:33 xubuntu kernel: [    0.118571] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 17 15:10:33 xubuntu kernel: [    0.118575] pci 0000:00:0d.0: PME# disabled
Aug 17 15:10:33 xubuntu kernel: [    0.118603] pci 0000:00:1e.0: [10de:01e8] type 1 class 0x000604
Aug 17 15:10:33 xubuntu kernel: [    0.118663] pci 0000:01:08.0: [1106:3149] type 0 class 0x000104
Aug 17 15:10:33 xubuntu kernel: [    0.118683] pci 0000:01:08.0: reg 10: [io  0xa000-0xa007]
Aug 17 15:10:33 xubuntu kernel: [    0.118696] pci 0000:01:08.0: reg 14: [io  0xa400-0xa403]
Aug 17 15:10:33 xubuntu kernel: [    0.118708] pci 0000:01:08.0: reg 18: [io  0xa800-0xa807]
Aug 17 15:10:33 xubuntu kernel: [    0.118720] pci 0000:01:08.0: reg 1c: [io  0xac00-0xac03]
Aug 17 15:10:33 xubuntu kernel: [    0.118732] pci 0000:01:08.0: reg 20: [io  0xb000-0xb00f]
Aug 17 15:10:33 xubuntu kernel: [    0.118744] pci 0000:01:08.0: reg 24: [io  0xb400-0xb4ff]
Aug 17 15:10:33 xubuntu kernel: [    0.118757] pci 0000:01:08.0: reg 30: [mem 0x00000000-0x0000ffff pref]
Aug 17 15:10:33 xubuntu kernel: [    0.118826] pci 0000:00:08.0: PCI bridge to [bus 01-01]
Aug 17 15:10:33 xubuntu kernel: [    0.118831] pci 0000:00:08.0:   bridge window [io  0xa000-0xcfff]
Aug 17 15:10:33 xubuntu kernel: [    0.118836] pci 0000:00:08.0:   bridge window [mem 0xee000000-0xeeffffff]
Aug 17 15:10:33 xubuntu kernel: [    0.118860] pci 0000:02:00.0: [10de:01f0] type 0 class 0x000300
Aug 17 15:10:33 xubuntu kernel: [    0.118875] pci 0000:02:00.0: reg 10: [mem 0xec000000-0xecffffff]
Aug 17 15:10:33 xubuntu kernel: [    0.118883] pci 0000:02:00.0: reg 14: [mem 0xe4000000-0xe7ffffff pref]
Aug 17 15:10:33 xubuntu kernel: [    0.118892] pci 0000:02:00.0: reg 18: [mem 0xe8000000-0xe807ffff pref]
Aug 17 15:10:33 xubuntu kernel: [    0.118916] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Aug 17 15:10:33 xubuntu kernel: [    0.118971] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
Aug 17 15:10:33 xubuntu kernel: [    0.118977] pci 0000:00:1e.0:   bridge window [mem 0xec000000-0xedffffff]
Aug 17 15:10:33 xubuntu kernel: [    0.118981] pci 0000:00:1e.0:   bridge window [mem 0xe4000000-0xebffffff pref]
Aug 17 15:10:33 xubuntu kernel: [    0.118992] pci_bus 0000:00: on NUMA node 0
Aug 17 15:10:33 xubuntu kernel: [    0.118996] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 17 15:10:33 xubuntu kernel: [    0.119115] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Aug 17 15:10:33 xubuntu kernel: [    0.119230] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
Aug 17 15:10:33 xubuntu kernel: [    0.119333]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
Aug 17 15:10:33 xubuntu kernel: [    0.153495] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.153551] ACPI: PCI Interrupt Link [LNK1] (IRQs *0 20)
Aug 17 15:10:33 xubuntu kernel: [    0.153597] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.153650] ACPI: PCI Interrupt Link [LNK2] (IRQs *0 20), disabled.
Aug 17 15:10:33 xubuntu kernel: [    0.153695] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.153747] ACPI: PCI Interrupt Link [LNK3] (IRQs *0 20), disabled.
Aug 17 15:10:33 xubuntu kernel: [    0.153792] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.153842] ACPI: PCI Interrupt Link [LNK4] (IRQs *0 20), disabled.
Aug 17 15:10:33 xubuntu kernel: [    0.153886] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.153937] ACPI: PCI Interrupt Link [LNK5] (IRQs *0 20)
Aug 17 15:10:33 xubuntu kernel: [    0.153981] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.154032] ACPI: PCI Interrupt Link [LUBA] (IRQs *0 20)
Aug 17 15:10:33 xubuntu kernel: [    0.154075] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.154126] ACPI: PCI Interrupt Link [LUBB] (IRQs *0 20)
Aug 17 15:10:33 xubuntu kernel: [    0.154170] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.154220] ACPI: PCI Interrupt Link [LMAC] (IRQs *0 20)
Aug 17 15:10:33 xubuntu kernel: [    0.154264] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.154315] ACPI: PCI Interrupt Link [LAPU] (IRQs *0 20)
Aug 17 15:10:33 xubuntu kernel: [    0.154366] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.154417] ACPI: PCI Interrupt Link [LACI] (IRQs *0 20)
Aug 17 15:10:33 xubuntu kernel: [    0.154461] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.154511] ACPI: PCI Interrupt Link [LMCI] (IRQs *0 20), disabled.
Aug 17 15:10:33 xubuntu kernel: [    0.154556] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.154607] ACPI: PCI Interrupt Link [LSMB] (IRQs *0 20)
Aug 17 15:10:33 xubuntu kernel: [    0.154651] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.154702] ACPI: PCI Interrupt Link [LUB2] (IRQs *0 20)
Aug 17 15:10:33 xubuntu kernel: [    0.154751] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.154802] ACPI: PCI Interrupt Link [LFIR] (IRQs *0 20)
Aug 17 15:10:33 xubuntu kernel: [    0.154851] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.154902] ACPI: PCI Interrupt Link [L3CM] (IRQs *0 20), disabled.
Aug 17 15:10:33 xubuntu kernel: [    0.154946] ACPI: Invalid _PRS IRQ 0
Aug 17 15:10:33 xubuntu kernel: [    0.154997] ACPI: PCI Interrupt Link [LIDE] (IRQs *0 20), disabled.
Aug 17 15:10:33 xubuntu kernel: [    0.155064] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
Aug 17 15:10:33 xubuntu kernel: [    0.155117] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
Aug 17 15:10:33 xubuntu kernel: [    0.155169] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
Aug 17 15:10:33 xubuntu kernel: [    0.155221] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
Aug 17 15:10:33 xubuntu kernel: [    0.155273] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
Aug 17 15:10:33 xubuntu kernel: [    0.155360] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
Aug 17 15:10:33 xubuntu kernel: [    0.155448] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
Aug 17 15:10:33 xubuntu kernel: [    0.155533] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
Aug 17 15:10:33 xubuntu kernel: [    0.155619] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0
Aug 17 15:10:33 xubuntu kernel: [    0.155704] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
Aug 17 15:10:33 xubuntu kernel: [    0.155788] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
Aug 17 15:10:33 xubuntu kernel: [    0.155843] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
Aug 17 15:10:33 xubuntu kernel: [    0.155926] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
Aug 17 15:10:33 xubuntu kernel: [    0.156022] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0
Aug 17 15:10:33 xubuntu kernel: [    0.156110] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
Aug 17 15:10:33 xubuntu kernel: [    0.156195] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Aug 17 15:10:33 xubuntu kernel: [    0.156389] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
Aug 17 15:10:33 xubuntu kernel: [    0.156392] vgaarb: loaded
Aug 17 15:10:33 xubuntu kernel: [    0.156394] vgaarb: bridge control possible 0000:02:00.0
Aug 17 15:10:33 xubuntu kernel: [    0.156587] i2c-core: driver [aat2870] using legacy suspend method
Aug 17 15:10:33 xubuntu kernel: [    0.156590] i2c-core: driver [aat2870] using legacy resume method
Aug 17 15:10:33 xubuntu kernel: [    0.156722] SCSI subsystem initialized
Aug 17 15:10:33 xubuntu kernel: [    0.156826] libata version 3.00 loaded.
Aug 17 15:10:33 xubuntu kernel: [    0.156915] usbcore: registered new interface driver usbfs
Aug 17 15:10:33 xubuntu kernel: [    0.156933] usbcore: registered new interface driver hub
Aug 17 15:10:33 xubuntu kernel: [    0.157355] usbcore: registered new device driver usb
Aug 17 15:10:33 xubuntu kernel: [    0.157502] PCI: Using ACPI for IRQ routing
Aug 17 15:10:33 xubuntu kernel: [    0.157508] PCI: pci_cache_line_size set to 32 bytes
Aug 17 15:10:33 xubuntu kernel: [    0.157583] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
Aug 17 15:10:33 xubuntu kernel: [    0.157586] reserve RAM buffer: 000000003dff0000 - 000000003fffffff 
Aug 17 15:10:33 xubuntu kernel: [    0.157745] NetLabel: Initializing
Aug 17 15:10:33 xubuntu kernel: [    0.157747] NetLabel:  domain hash size = 128
Aug 17 15:10:33 xubuntu kernel: [    0.157749] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 17 15:10:33 xubuntu kernel: [    0.157767] NetLabel:  unlabeled traffic allowed by default
Aug 17 15:10:33 xubuntu kernel: [    0.171126] AppArmor: AppArmor Filesystem Enabled
Aug 17 15:10:33 xubuntu kernel: [    0.171187] pnp: PnP ACPI init
Aug 17 15:10:33 xubuntu kernel: [    0.171222] ACPI: bus type pnp registered
Aug 17 15:10:33 xubuntu kernel: [    0.171563] pnp 00:00: [io  0x4000-0x407f]
Aug 17 15:10:33 xubuntu kernel: [    0.171566] pnp 00:00: [io  0x4080-0x40ff]
Aug 17 15:10:33 xubuntu kernel: [    0.171569] pnp 00:00: [io  0x4400-0x447f]
Aug 17 15:10:33 xubuntu kernel: [    0.171572] pnp 00:00: [io  0x4480-0x44ff]
Aug 17 15:10:33 xubuntu kernel: [    0.171574] pnp 00:00: [io  0x4200-0x427f]
Aug 17 15:10:33 xubuntu kernel: [    0.171576] pnp 00:00: [io  0x4280-0x42ff]
Aug 17 15:10:33 xubuntu kernel: [    0.171661] system 00:00: [io  0x4000-0x407f] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.171665] system 00:00: [io  0x4080-0x40ff] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.171669] system 00:00: [io  0x4400-0x447f] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.171672] system 00:00: [io  0x4480-0x44ff] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.171675] system 00:00: [io  0x4200-0x427f] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.171678] system 00:00: [io  0x4280-0x42ff] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.171683] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 17 15:10:33 xubuntu kernel: [    0.171698] pnp 00:01: [io  0x5000-0x503f]
Aug 17 15:10:33 xubuntu kernel: [    0.171701] pnp 00:01: [io  0x5100-0x513f]
Aug 17 15:10:33 xubuntu kernel: [    0.171750] system 00:01: [io  0x5000-0x503f] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.171754] system 00:01: [io  0x5100-0x513f] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.171758] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 17 15:10:33 xubuntu kernel: [    0.171952] pnp 00:02: [mem 0x000d1800-0x000d3fff]
Aug 17 15:10:33 xubuntu kernel: [    0.171955] pnp 00:02: [mem 0x000f0000-0x000f7fff]
Aug 17 15:10:33 xubuntu kernel: [    0.171958] pnp 00:02: [mem 0x000f8000-0x000fbfff]
Aug 17 15:10:33 xubuntu kernel: [    0.171961] pnp 00:02: [mem 0x000fc000-0x000fffff]
Aug 17 15:10:33 xubuntu kernel: [    0.171963] pnp 00:02: [mem 0x3dff0000-0x3dffffff]
Aug 17 15:10:33 xubuntu kernel: [    0.171966] pnp 00:02: [mem 0xffff0000-0xffffffff]
Aug 17 15:10:33 xubuntu kernel: [    0.171969] pnp 00:02: [mem 0x00000000-0x0009ffff]
Aug 17 15:10:33 xubuntu kernel: [    0.171971] pnp 00:02: [mem 0x00100000-0x3dfeffff]
Aug 17 15:10:33 xubuntu kernel: [    0.171974] pnp 00:02: [mem 0xfec00000-0xfec00fff]
Aug 17 15:10:33 xubuntu kernel: [    0.171977] pnp 00:02: [mem 0xfee00000-0xfee00fff]
Aug 17 15:10:33 xubuntu kernel: [    0.172066] system 00:02: [mem 0x000d1800-0x000d3fff] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.172071] system 00:02: [mem 0x000f0000-0x000f7fff] could not be reserved
Aug 17 15:10:33 xubuntu kernel: [    0.172075] system 00:02: [mem 0x000f8000-0x000fbfff] could not be reserved
Aug 17 15:10:33 xubuntu kernel: [    0.172078] system 00:02: [mem 0x000fc000-0x000fffff] could not be reserved
Aug 17 15:10:33 xubuntu kernel: [    0.172082] system 00:02: [mem 0x3dff0000-0x3dffffff] could not be reserved
Aug 17 15:10:33 xubuntu kernel: [    0.172086] system 00:02: [mem 0xffff0000-0xffffffff] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.172089] system 00:02: [mem 0x00000000-0x0009ffff] could not be reserved
Aug 17 15:10:33 xubuntu kernel: [    0.172093] system 00:02: [mem 0x00100000-0x3dfeffff] could not be reserved
Aug 17 15:10:33 xubuntu kernel: [    0.172097] system 00:02: [mem 0xfec00000-0xfec00fff] could not be reserved
Aug 17 15:10:33 xubuntu kernel: [    0.172100] system 00:02: [mem 0xfee00000-0xfee00fff] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.172105] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
Aug 17 15:10:33 xubuntu kernel: [    0.172177] pnp 00:03: [bus 00-ff]
Aug 17 15:10:33 xubuntu kernel: [    0.172180] pnp 00:03: [io  0x0cf8-0x0cff]
Aug 17 15:10:33 xubuntu kernel: [    0.172183] pnp 00:03: [io  0x0cf0-0x0cf3]
Aug 17 15:10:33 xubuntu kernel: [    0.172186] pnp 00:03: [io  0x0000-0x0cef window]
Aug 17 15:10:33 xubuntu kernel: [    0.172189] pnp 00:03: [io  0x0d00-0xffff window]
Aug 17 15:10:33 xubuntu kernel: [    0.172192] pnp 00:03: [mem 0x000a0000-0x000bffff window]
Aug 17 15:10:33 xubuntu kernel: [    0.172195] pnp 00:03: [mem 0x000c0000-0x000dffff window]
Aug 17 15:10:33 xubuntu kernel: [    0.172198] pnp 00:03: [mem 0x3e000000-0xfebfffff window]
Aug 17 15:10:33 xubuntu kernel: [    0.172270] pnp 00:03: Plug and Play ACPI device, IDs PNP0a03 (active)
Aug 17 15:10:33 xubuntu kernel: [    0.172839] pnp 00:04: [io  0x0010-0x001f]
Aug 17 15:10:33 xubuntu kernel: [    0.172842] pnp 00:04: [io  0x0022-0x003f]
Aug 17 15:10:33 xubuntu kernel: [    0.172845] pnp 00:04: [io  0x0044-0x005f]
Aug 17 15:10:33 xubuntu kernel: [    0.172847] pnp 00:04: [io  0x0062-0x0063]
Aug 17 15:10:33 xubuntu kernel: [    0.172850] pnp 00:04: [io  0x0065-0x006f]
Aug 17 15:10:33 xubuntu kernel: [    0.172852] pnp 00:04: [io  0x0074-0x007f]
Aug 17 15:10:33 xubuntu kernel: [    0.172855] pnp 00:04: [io  0x0091-0x0093]
Aug 17 15:10:33 xubuntu kernel: [    0.172857] pnp 00:04: [io  0x00a2-0x00bf]
Aug 17 15:10:33 xubuntu kernel: [    0.172860] pnp 00:04: [io  0x00e0-0x00ef]
Aug 17 15:10:33 xubuntu kernel: [    0.172862] pnp 00:04: [io  0x0b78-0x0b7b]
Aug 17 15:10:33 xubuntu kernel: [    0.172865] pnp 00:04: [io  0x0f78-0x0f7b]
Aug 17 15:10:33 xubuntu kernel: [    0.172867] pnp 00:04: [io  0x0a78-0x0a7b]
Aug 17 15:10:33 xubuntu kernel: [    0.172870] pnp 00:04: [io  0x0e78-0x0e7b]
Aug 17 15:10:33 xubuntu kernel: [    0.172879] pnp 00:04: [io  0x0bbc-0x0bbf]
Aug 17 15:10:33 xubuntu kernel: [    0.172881] pnp 00:04: [io  0x0fbc-0x0fbf]
Aug 17 15:10:33 xubuntu kernel: [    0.172884] pnp 00:04: [io  0x04d0-0x04d1]
Aug 17 15:10:33 xubuntu kernel: [    0.172886] pnp 00:04: [io  0x0294-0x0297]
Aug 17 15:10:33 xubuntu kernel: [    0.172889] pnp 00:04: [io  0x0200]
Aug 17 15:10:33 xubuntu kernel: [    0.173349] system 00:04: [io  0x0b78-0x0b7b] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.173353] system 00:04: [io  0x0f78-0x0f7b] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.173356] system 00:04: [io  0x0a78-0x0a7b] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.173359] system 00:04: [io  0x0e78-0x0e7b] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.173362] system 00:04: [io  0x0bbc-0x0bbf] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.173366] system 00:04: [io  0x0fbc-0x0fbf] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.173369] system 00:04: [io  0x04d0-0x04d1] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.173372] system 00:04: [io  0x0294-0x0297] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.173375] system 00:04: [io  0x0200] has been reserved
Aug 17 15:10:33 xubuntu kernel: [    0.173379] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 17 15:10:33 xubuntu kernel: [    0.173396] pnp 00:05: [dma 4]
Aug 17 15:10:33 xubuntu kernel: [    0.173399] pnp 00:05: [io  0x0000-0x000f]
Aug 17 15:10:33 xubuntu kernel: [    0.173401] pnp 00:05: [io  0x0080-0x0090]
Aug 17 15:10:33 xubuntu kernel: [    0.173404] pnp 00:05: [io  0x0094-0x009f]
Aug 17 15:10:33 xubuntu kernel: [    0.173406] pnp 00:05: [io  0x00c0-0x00df]
Aug 17 15:10:33 xubuntu kernel: [    0.173452] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
Aug 17 15:10:33 xubuntu kernel: [    0.173467] pnp 00:06: [io  0x0070-0x0073]
Aug 17 15:10:33 xubuntu kernel: [    0.173486] pnp 00:06: [irq 8]
Aug 17 15:10:33 xubuntu kernel: [    0.173532] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Aug 17 15:10:33 xubuntu kernel: [    0.173544] pnp 00:07: [io  0x0061]
Aug 17 15:10:33 xubuntu kernel: [    0.173596] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
Aug 17 15:10:33 xubuntu kernel: [    0.173609] pnp 00:08: [io  0x00f0-0x00ff]
Aug 17 15:10:33 xubuntu kernel: [    0.173616] pnp 00:08: [irq 13]
Aug 17 15:10:33 xubuntu kernel: [    0.173663] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
Aug 17 15:10:33 xubuntu kernel: [    0.173803] pnp 00:09: [io  0x03f0-0x03f5]
Aug 17 15:10:33 xubuntu kernel: [    0.173806] pnp 00:09: [io  0x03f7]
Aug 17 15:10:33 xubuntu kernel: [    0.173812] pnp 00:09: [irq 6]
Aug 17 15:10:33 xubuntu kernel: [    0.173815] pnp 00:09: [dma 2]
Aug 17 15:10:33 xubuntu kernel: [    0.173885] pnp 00:09: Plug and Play ACPI device, IDs PNP0700 (active)
Aug 17 15:10:33 xubuntu kernel: [    0.174087] pnp 00:0a: [io  0x03f8-0x03ff]
Aug 17 15:10:33 xubuntu kernel: [    0.174094] pnp 00:0a: [irq 4]
Aug 17 15:10:33 xubuntu kernel: [    0.174186] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
Aug 17 15:10:33 xubuntu kernel: [    0.174641] pnp 00:0b: [io  0x0378-0x037f]
Aug 17 15:10:34 xubuntu avahi-daemon[1340]: Found user 'avahi' (UID 106) and group 'avahi' (GID 118).
Aug 17 15:10:34 xubuntu avahi-daemon[1340]: Successfully dropped root privileges.
Aug 17 15:10:34 xubuntu avahi-daemon[1340]: avahi-daemon 0.6.30 starting up.
Aug 17 15:10:34 xubuntu kernel: [    0.174644] pnp 00:0b: [io  0x0778-0x077b]
Aug 17 15:10:34 xubuntu kernel: [    0.174650] pnp 00:0b: [irq 7]
Aug 17 15:10:34 xubuntu kernel: [    0.174728] pnp 00:0b: Plug and Play ACPI device, IDs PNP0400 (active)
Aug 17 15:10:34 xubuntu kernel: [    0.174852] pnp 00:0c: [irq 12]
Aug 17 15:10:34 xubuntu kernel: [    0.174908] pnp 00:0c: Plug and Play ACPI device, IDs PNP0f13 (active)
Aug 17 15:10:34 xubuntu kernel: [    0.174941] pnp 00:0d: [io  0x0060]
Aug 17 15:10:34 xubuntu kernel: [    0.174944] pnp 00:0d: [io  0x0064]
Aug 17 15:10:34 xubuntu kernel: [    0.174951] pnp 00:0d: [irq 1]
Aug 17 15:10:34 xubuntu kernel: [    0.175002] pnp 00:0d: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Aug 17 15:10:34 xubuntu kernel: [    0.175114] pnp: PnP ACPI: found 14 devices
Aug 17 15:10:34 xubuntu kernel: [    0.175117] ACPI: ACPI bus type pnp unregistered
Aug 17 15:10:34 xubuntu kernel: [    0.175121] PnPBIOS: Disabled by ACPI PNP
Aug 17 15:10:34 xubuntu kernel: [    0.213328] Switching to clocksource acpi_pm
Aug 17 15:10:34 xubuntu kernel: [    0.213359] PCI: max bus depth: 1 pci_try_num: 2
Aug 17 15:10:34 xubuntu kernel: [    0.213387] pci 0000:00:08.0: BAR 15: assigned [mem 0x40000000-0x400fffff pref]
Aug 17 15:10:34 xubuntu kernel: [    0.213393] pci 0000:01:08.0: BAR 6: assigned [mem 0x40000000-0x4000ffff pref]
Aug 17 15:10:34 xubuntu kernel: [    0.213397] pci 0000:00:08.0: PCI bridge to [bus 01-01]
Aug 17 15:10:34 xubuntu kernel: [    0.213401] pci 0000:00:08.0:   bridge window [io  0xa000-0xcfff]
Aug 17 15:10:34 xubuntu kernel: [    0.213408] pci 0000:00:08.0:   bridge window [mem 0xee000000-0xeeffffff]
Aug 17 15:10:34 xubuntu kernel: [    0.213413] pci 0000:00:08.0:   bridge window [mem 0x40000000-0x400fffff pref]
Aug 17 15:10:34 xubuntu kernel: [    0.213421] pci 0000:02:00.0: BAR 6: assigned [mem 0xe8080000-0xe809ffff pref]
Aug 17 15:10:34 xubuntu kernel: [    0.213424] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
Aug 17 15:10:34 xubuntu kernel: [    0.213429] pci 0000:00:1e.0:   bridge window [mem 0xec000000-0xedffffff]
Aug 17 15:10:34 xubuntu kernel: [    0.213433] pci 0000:00:1e.0:   bridge window [mem 0xe4000000-0xebffffff pref]
Aug 17 15:10:34 xubuntu kernel: [    0.213447] pci 0000:00:08.0: setting latency timer to 64
Aug 17 15:10:34 xubuntu kernel: [    0.213455] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Aug 17 15:10:34 xubuntu kernel: [    0.213459] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
Aug 17 15:10:34 xubuntu kernel: [    0.213462] pci_bus 0000:01: resource 0 [io  0xa000-0xcfff]
Aug 17 15:10:34 xubuntu kernel: [    0.213465] pci_bus 0000:01: resource 1 [mem 0xee000000-0xeeffffff]
Aug 17 15:10:34 xubuntu kernel: [    0.213468] pci_bus 0000:01: resource 2 [mem 0x40000000-0x400fffff pref]
Aug 17 15:10:34 xubuntu kernel: [    0.213472] pci_bus 0000:02: resource 1 [mem 0xec000000-0xedffffff]
Aug 17 15:10:34 xubuntu kernel: [    0.213475] pci_bus 0000:02: resource 2 [mem 0xe4000000-0xebffffff pref]
Aug 17 15:10:34 xubuntu kernel: [    0.213545] NET: Registered protocol family 2
Aug 17 15:10:34 xubuntu kernel: [    0.213629] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 17 15:10:34 xubuntu kernel: [    0.214065] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 17 15:10:34 xubuntu kernel: [    0.215643] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 17 15:10:34 xubuntu kernel: [    0.215643] TCP: Hash tables configured (established 131072 bind 65536)
Aug 17 15:10:34 xubuntu kernel: [    0.215643] TCP reno registered
Aug 17 15:10:34 xubuntu kernel: [    0.215643] UDP hash table entries: 512 (order: 2, 16384 bytes)
Aug 17 15:10:34 xubuntu kernel: [    0.215643] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Aug 17 15:10:34 xubuntu kernel: [    0.215643] NET: Registered protocol family 1
Aug 17 15:10:34 xubuntu kernel: [    0.215997] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
Aug 17 15:10:34 xubuntu kernel: [    0.216040] pci 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, high) -> IRQ 22
Aug 17 15:10:34 xubuntu kernel: [    0.288031] pci 0000:00:02.0: PCI INT A disabled
Aug 17 15:10:34 xubuntu kernel: [    0.288187] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
Aug 17 15:10:34 xubuntu kernel: [    0.288198] pci 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 21 (level, high) -> IRQ 21
Aug 17 15:10:34 xubuntu kernel: [    0.360026] pci 0000:00:02.1: PCI INT B disabled
Aug 17 15:10:34 xubuntu kernel: [    0.360180] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
Aug 17 15:10:34 xubuntu kernel: [    0.360190] pci 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 20 (level, high) -> IRQ 20
Aug 17 15:10:34 xubuntu kernel: [    0.360217] pci 0000:00:02.2: PCI INT C disabled
Aug 17 15:10:34 xubuntu kernel: [    0.360268] pci 0000:02:00.0: Boot video device
Aug 17 15:10:34 xubuntu kernel: [    0.360272] PCI: CLS 0 bytes, default 32
Aug 17 15:10:34 xubuntu kernel: [    0.360858] audit: initializing netlink socket (disabled)
Aug 17 15:10:34 xubuntu kernel: [    0.360873] type=2000 audit(1345216209.356:1): initialized
Aug 17 15:10:34 xubuntu kernel: [    0.384856] Trying to unpack rootfs image as initramfs...
Aug 17 15:10:34 xubuntu kernel: [    3.344020] Refined TSC clocksource calibration: 2162.741 MHz.
Aug 17 15:10:34 xubuntu kernel: [    3.350158] highmem bounce pool size: 64 pages
Aug 17 15:10:34 xubuntu kernel: [    3.350168] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Aug 17 15:10:34 xubuntu kernel: [    3.364155] VFS: Disk quotas dquot_6.5.2
Aug 17 15:10:34 xubuntu kernel: [    3.364239] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 17 15:10:34 xubuntu kernel: [    3.365080] fuse init (API version 7.17)
Aug 17 15:10:34 xubuntu kernel: [    3.365213] msgmni has been set to 1700
Aug 17 15:10:34 xubuntu kernel: [    3.365684] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug 17 15:10:34 xubuntu kernel: [    3.365726] io scheduler noop registered
Aug 17 15:10:34 xubuntu kernel: [    3.365729] io scheduler deadline registered
Aug 17 15:10:34 xubuntu kernel: [    3.365738] io scheduler cfq registered (default)
Aug 17 15:10:34 xubuntu kernel: [    3.365973] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 17 15:10:34 xubuntu kernel: [    3.366011] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 17 15:10:34 xubuntu kernel: [    3.366222] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Aug 17 15:10:34 xubuntu kernel: [    3.366231] ACPI: Power Button [PWRB]
Aug 17 15:10:34 xubuntu kernel: [    3.366299] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Aug 17 15:10:34 xubuntu kernel: [    3.366305] ACPI: Sleep Button [SLPB]
Aug 17 15:10:34 xubuntu kernel: [    3.366375] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Aug 17 15:10:34 xubuntu kernel: [    3.366379] ACPI: Power Button [PWRF]
Aug 17 15:10:34 xubuntu kernel: [    3.366446] ACPI: Fan [FAN] (on)
Aug 17 15:10:34 xubuntu kernel: [    3.369446] thermal LNXTHERM:00: registered as thermal_zone0
Aug 17 15:10:34 xubuntu kernel: [    3.369450] ACPI: Thermal Zone [THRM] (42 C)
Aug 17 15:10:34 xubuntu kernel: [    3.369505] ERST: Table is not found!
Aug 17 15:10:34 xubuntu kernel: [    3.369508] GHES: HEST is not enabled!
Aug 17 15:10:34 xubuntu kernel: [    3.369675] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug 17 15:10:34 xubuntu kernel: [    3.390165] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 17 15:10:34 xubuntu kernel: [    3.390199] isapnp: Scanning for PnP cards...
Aug 17 15:10:34 xubuntu kernel: [    3.461477] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 17 15:10:34 xubuntu kernel: [    3.461787] Linux agpgart interface v0.103
Aug 17 15:10:34 xubuntu kernel: [    3.461889] agpgart: Detected NVIDIA nForce2 chipset
Aug 17 15:10:34 xubuntu kernel: [    3.509904] agpgart-nvidia 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
Aug 17 15:10:34 xubuntu kernel: [    3.511950] brd: module loaded
Aug 17 15:10:34 xubuntu kernel: [    3.513037] loop: module loaded
Aug 17 15:10:34 xubuntu kernel: [    3.513340] pata_acpi 0000:00:09.0: power state changed by ACPI to D0
Aug 17 15:10:34 xubuntu kernel: [    3.513346] pata_acpi 0000:00:09.0: power state changed by ACPI to D0
Aug 17 15:10:34 xubuntu kernel: [    3.513412] pata_acpi 0000:00:09.0: setting latency timer to 64
Aug 17 15:10:34 xubuntu kernel: [    3.513949] Fixed MDIO Bus: probed
Aug 17 15:10:34 xubuntu kernel: [    3.513980] tun: Universal TUN/TAP device driver, 1.6
Aug 17 15:10:34 xubuntu kernel: [    3.513983] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 17 15:10:34 xubuntu kernel: [    3.514049] PPP generic driver version 2.4.2
Aug 17 15:10:34 xubuntu kernel: [    3.514194] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 17 15:10:34 xubuntu kernel: [    3.514221] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 20 (level, high) -> IRQ 20
Aug 17 15:10:34 xubuntu kernel: [    3.514248] ehci_hcd 0000:00:02.2: setting latency timer to 64
Aug 17 15:10:34 xubuntu kernel: [    3.514252] ehci_hcd 0000:00:02.2: EHCI Host Controller
Aug 17 15:10:34 xubuntu kernel: [    3.514308] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
Aug 17 15:10:34 xubuntu kernel: [    3.514353] ehci_hcd 0000:00:02.2: debug port 1
Aug 17 15:10:34 xubuntu kernel: [    3.514363] ehci_hcd 0000:00:02.2: cache line size of 32 is not supported
Aug 17 15:10:34 xubuntu kernel: [    3.514395] ehci_hcd 0000:00:02.2: irq 20, io mem 0xef086000
Aug 17 15:10:34 xubuntu kernel: [    3.558042] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
Aug 17 15:10:34 xubuntu kernel: [    3.601906] hub 1-0:1.0: USB hub found
Aug 17 15:10:34 xubuntu kernel: [    3.601914] hub 1-0:1.0: 6 ports detected
Aug 17 15:10:34 xubuntu kernel: [    3.602011] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 17 15:10:34 xubuntu kernel: [    3.602037] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, high) -> IRQ 22
Aug 17 15:10:34 xubuntu kernel: [    3.602050] ohci_hcd 0000:00:02.0: setting latency timer to 64
Aug 17 15:10:34 xubuntu kernel: [    3.602054] ohci_hcd 0000:00:02.0: OHCI Host Controller
Aug 17 15:10:34 xubuntu kernel: [    3.602105] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Aug 17 15:10:34 xubuntu kernel: [    3.602139] ohci_hcd 0000:00:02.0: irq 22, io mem 0xef080000
Aug 17 15:10:34 xubuntu kernel: [    3.734815] hub 2-0:1.0: USB hub found
Aug 17 15:10:34 xubuntu kernel: [    3.734823] hub 2-0:1.0: 3 ports detected
Aug 17 15:10:34 xubuntu kernel: [    3.734906] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 21 (level, high) -> IRQ 21
Aug 17 15:10:34 xubuntu kernel: [    3.734920] ohci_hcd 0000:00:02.1: setting latency timer to 64
Aug 17 15:10:34 xubuntu kernel: [    3.734923] ohci_hcd 0000:00:02.1: OHCI Host Controller
Aug 17 15:10:34 xubuntu kernel: [    3.734980] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
Aug 17 15:10:34 xubuntu kernel: [    3.735010] ohci_hcd 0000:00:02.1: irq 21, io mem 0xef083000
Aug 17 15:10:34 xubuntu kernel: [    3.778628] isapnp: No Plug & Play device found
Aug 17 15:10:34 xubuntu kernel: [    3.790326] hub 3-0:1.0: USB hub found
Aug 17 15:10:34 xubuntu kernel: [    3.790338] hub 3-0:1.0: 3 ports detected
Aug 17 15:10:34 xubuntu kernel: [    3.790468] uhci_hcd: USB Universal Host Controller Interface driver
Aug 17 15:10:34 xubuntu kernel: [    3.790585] usbcore: registered new interface driver libusual
Aug 17 15:10:34 xubuntu kernel: [    3.790652] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 17 15:10:34 xubuntu kernel: [    3.796790] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 17 15:10:34 xubuntu kernel: [    3.796803] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 17 15:10:34 xubuntu kernel: [    3.796998] mousedev: PS/2 mouse device common for all mice
Aug 17 15:10:34 xubuntu kernel: [    3.797210] rtc_cmos 00:06: RTC can wake from S4
Aug 17 15:10:34 xubuntu kernel: [    3.797350] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Aug 17 15:10:34 xubuntu kernel: [    3.797378] rtc0: alarms up to one year, y3k, 242 bytes nvram
Aug 17 15:10:34 xubuntu kernel: [    3.797520] device-mapper: uevent: version 1.0.3
Aug 17 15:10:34 xubuntu kernel: [    3.797619] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
Aug 17 15:10:34 xubuntu kernel: [    3.797672] EISA: Probing bus 0 at eisa.0
Aug 17 15:10:34 xubuntu kernel: [    3.797698] Cannot allocate resource for EISA slot 4
Aug 17 15:10:34 xubuntu kernel: [    3.797701] Cannot allocate resource for EISA slot 5
Aug 17 15:10:34 xubuntu kernel: [    3.797718] EISA: Detected 0 cards.
Aug 17 15:10:34 xubuntu kernel: [    3.797732] cpufreq-nforce2: Detected nForce2 chipset revision A2
Aug 17 15:10:34 xubuntu kernel: [    3.797734] cpufreq-nforce2: FSB changing is maybe unstable and can lead to crashes and data loss.
Aug 17 15:10:34 xubuntu kernel: [    3.797744] cpufreq-nforce2: FSB currently at 166 MHz, FID 13.0
Aug 17 15:10:34 xubuntu kernel: [    3.797777] Marking TSC unstable due to cpufreq changes
Aug 17 15:10:34 xubuntu kernel: [    3.798642] cpuidle: using governor ladder
Aug 17 15:10:34 xubuntu kernel: [    3.798645] cpuidle: using governor menu
Aug 17 15:10:34 xubuntu kernel: [    3.798647] EFI Variables Facility v0.08 2004-May-17
Aug 17 15:10:34 xubuntu kernel: [    3.798918] TCP cubic registered
Aug 17 15:10:34 xubuntu kernel: [    3.799122] NET: Registered protocol family 10
Aug 17 15:10:34 xubuntu kernel: [    3.799767] NET: Registered protocol family 17
Aug 17 15:10:34 xubuntu kernel: [    3.799795] Registering the dns_resolver key type
Aug 17 15:10:34 xubuntu kernel: [    3.799827] Using IPI No-Shortcut mode
Aug 17 15:10:34 xubuntu kernel: [    3.804209] PM: Hibernation image not present or could not be loaded.
Aug 17 15:10:34 xubuntu kernel: [    3.804234] registered taskstats version 1
Aug 17 15:10:34 xubuntu kernel: [    5.039611] sched: RT throttling activated
Aug 17 15:10:34 xubuntu kernel: [    5.094686] Freeing initrd memory: 15176k freed
Aug 17 15:10:34 xubuntu kernel: [    5.124846]   Magic number: 8:496:184
Aug 17 15:10:34 xubuntu kernel: [    5.124933] thermal LNXTHERM:00: hash matches
Aug 17 15:10:34 xubuntu kernel: [    5.125001] rtc_cmos 00:06: setting system clock to 2012-08-17 15:10:15 UTC (1345216215)
Aug 17 15:10:34 xubuntu kernel: [    5.125006] powernow-k8: Processor cpuid 6a0 not supported
Aug 17 15:10:34 xubuntu kernel: [    5.125026] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 17 15:10:34 xubuntu kernel: [    5.125028] EDD information not available.
Aug 17 15:10:34 xubuntu kernel: [    5.125198] Freeing unused kernel memory: 712k freed
Aug 17 15:10:34 xubuntu kernel: [    5.126092] Write protecting the kernel text: 5628k
Aug 17 15:10:34 xubuntu kernel: [    5.126135] Write protecting the kernel read-only data: 2324k
Aug 17 15:10:34 xubuntu kernel: [    5.348610] Floppy drive(s): fd0 is 1.44M
Aug 17 15:10:34 xubuntu kernel: [    5.407886] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Aug 17 15:10:34 xubuntu kernel: [    5.418078] sata_via 0000:01:08.0: version 2.6
Aug 17 15:10:34 xubuntu kernel: [    5.424629] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
Aug 17 15:10:34 xubuntu kernel: [    5.424646] forcedeth 0000:00:04.0: PCI INT A -> Link[APCH] -> GSI 22 (level, high) -> IRQ 22
Aug 17 15:10:34 xubuntu kernel: [    5.424655] forcedeth 0000:00:04.0: setting latency timer to 64
Aug 17 15:10:34 xubuntu kernel: [    5.433924] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Aug 17 15:10:34 xubuntu kernel: [    5.433947] sata_via 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, high) -> IRQ 16
Aug 17 15:10:34 xubuntu kernel: [    5.434017] sata_via 0000:01:08.0: routed to hard irq line 11
Aug 17 15:10:34 xubuntu kernel: [    5.436536] scsi0 : sata_via
Aug 17 15:10:34 xubuntu kernel: [    5.439984] wmi: Mapper loaded
Aug 17 15:10:34 xubuntu kernel: [    5.440075] scsi1 : sata_via
Aug 17 15:10:34 xubuntu kernel: [    5.440167] ata1: SATA max UDMA/133 cmd 0xa000 ctl 0xa400 bmdma 0xb000 irq 16
Aug 17 15:10:34 xubuntu kernel: [    5.440171] ata2: SATA max UDMA/133 cmd 0xa800 ctl 0xac00 bmdma 0xb008 irq 16
Aug 17 15:10:34 xubuntu kernel: [    5.489929] Switching to clocksource tsc
Aug 17 15:10:34 xubuntu kernel: [    5.492464] Switching to clocksource acpi_pm
Aug 17 15:10:34 xubuntu kernel: [    5.496291] FDC 0 is a post-1991 82077
Aug 17 15:10:34 xubuntu kernel: [    5.510280] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Aug 17 15:10:34 xubuntu kernel: [    5.644027] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 17 15:10:34 xubuntu kernel: [    5.808327] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S203N, SB00, max UDMA/100
Aug 17 15:10:34 xubuntu kernel: [    5.812021] usb 1-2: new high-speed USB device number 3 using ehci_hcd
Aug 17 15:10:34 xubuntu kernel: [    5.824333] ata1.00: configured for UDMA/100
Aug 17 15:10:34 xubuntu kernel: [    5.825657] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203N  SB00 PQ: 0 ANSI: 5
Aug 17 15:10:34 xubuntu kernel: [    5.828923] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 17 15:10:34 xubuntu kernel: [    5.828927] cdrom: Uniform CD-ROM driver Revision: 3.20
Aug 17 15:10:34 xubuntu kernel: [    5.829108] sr 0:0:0:0: Attached scsi CD-ROM sr0
Aug 17 15:10:34 xubuntu kernel: [    5.829200] sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug 17 15:10:34 xubuntu kernel: [    5.948925] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:e0:4c:b9:b7:6a
Aug 17 15:10:34 xubuntu kernel: [    5.948931] forcedeth 0000:00:04.0: timirq lnktim desc-v1
Aug 17 15:10:34 xubuntu kernel: [    5.949076] pata_amd 0000:00:09.0: version 0.4.1
Aug 17 15:10:34 xubuntu kernel: [    5.949096] pata_amd 0000:00:09.0: power state changed by ACPI to D0
Aug 17 15:10:34 xubuntu kernel: [    5.949101] pata_amd 0000:00:09.0: power state changed by ACPI to D0
Aug 17 15:10:34 xubuntu kernel: [    5.949170] pata_amd 0000:00:09.0: setting latency timer to 64
Aug 17 15:10:34 xubuntu kernel: [    5.952743] scsi2 : pata_amd
Aug 17 15:10:34 xubuntu kernel: [    5.955909] usbcore: registered new interface driver uas
Aug 17 15:10:34 xubuntu kernel: [    5.955927] scsi3 : pata_amd
Aug 17 15:10:34 xubuntu kernel: [    5.956643] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Aug 17 15:10:34 xubuntu kernel: [    5.956648] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Aug 17 15:10:34 xubuntu kernel: [    5.957156] Initializing USB Mass Storage driver...
Aug 17 15:10:34 xubuntu kernel: [    5.957294] scsi4 : usb-storage 1-2:1.0
Aug 17 15:10:34 xubuntu kernel: [    5.957392] usbcore: registered new interface driver usb-storage
Aug 17 15:10:34 xubuntu kernel: [    5.957395] USB Mass Storage support registered.
Aug 17 15:10:34 xubuntu kernel: [    6.032027] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Aug 17 15:10:34 xubuntu kernel: [    6.176540] ata3.00: ATA-6: ST380011A, 8.01, max UDMA/100
Aug 17 15:10:34 xubuntu kernel: [    6.176544] ata3.00: 156301488 sectors, multi 16: LBA48 
Aug 17 15:10:34 xubuntu kernel: [    6.176555] ata3: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6000000) ACPI=0x3f01f (20:600:0x13)
Aug 17 15:10:34 xubuntu kernel: [    6.192447] ata3.00: configured for UDMA/100
Aug 17 15:10:34 xubuntu kernel: [    6.192609] scsi 2:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
Aug 17 15:10:34 xubuntu kernel: [    6.193033] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Aug 17 15:10:34 xubuntu kernel: [    6.193103] sd 2:0:0:0: [sda] Write Protect is off
Aug 17 15:10:34 xubuntu kernel: [    6.193107] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 17 15:10:34 xubuntu kernel: [    6.193136] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 15:10:34 xubuntu kernel: [    6.193882] sd 2:0:0:0: Attached scsi generic sg1 type 0
Aug 17 15:10:34 xubuntu kernel: [    6.224789]  sda: sda1 sda2 < sda5 sda6 >
Aug 17 15:10:34 xubuntu kernel: [    6.225419] sd 2:0:0:0: [sda] Attached SCSI disk
Aug 17 15:10:34 xubuntu kernel: [    6.312023] usb 2-1: new full-speed USB device number 2 using ohci_hcd
Aug 17 15:10:34 xubuntu kernel: [    6.369647] ACPI: PCI Interrupt Link [APCM] enabled at IRQ 21
Aug 17 15:10:34 xubuntu kernel: [    6.369658] firewire_ohci 0000:00:0d.0: PCI INT A -> Link[APCM] -> GSI 21 (level, high) -> IRQ 21
Aug 17 15:10:34 xubuntu kernel: [    6.369668] firewire_ohci 0000:00:0d.0: setting latency timer to 64
Aug 17 15:10:34 xubuntu kernel: [    6.385817] [drm] Initialized drm 1.1.0 20060810
Aug 17 15:10:34 xubuntu kernel: [    6.411105] VGA switcheroo: detected Optimus DSM method \ handle
Aug 17 15:10:34 xubuntu kernel: [    6.411284] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Aug 17 15:10:34 xubuntu kernel: [    6.411293] nouveau 0000:02:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, high) -> IRQ 16
Aug 17 15:10:34 xubuntu kernel: [    6.413319] [drm] nouveau 0000:02:00.0: Detected an NV10 generation card (0x01f000a5)
Aug 17 15:10:34 xubuntu kernel: [    6.413538] [drm] nouveau 0000:02:00.0: Attempting to load BIOS image from PRAMIN
Aug 17 15:10:34 xubuntu kernel: [    6.456987] [drm] nouveau 0000:02:00.0: ... BIOS checksum invalid
Aug 17 15:10:34 xubuntu kernel: [    6.456990] [drm] nouveau 0000:02:00.0: Attempting to load BIOS image from PROM
Aug 17 15:10:34 xubuntu kernel: [    6.456994] [drm] nouveau 0000:02:00.0: ... BIOS signature not found
Aug 17 15:10:34 xubuntu kernel: [    6.456997] [drm] nouveau 0000:02:00.0: Attempting to load BIOS image from PCIROM
Aug 17 15:10:34 xubuntu kernel: [    6.457382] [drm] nouveau 0000:02:00.0: ... appears to be valid
Aug 17 15:10:34 xubuntu kernel: [    6.457545] [drm] nouveau 0000:02:00.0: BMP BIOS found
Aug 17 15:10:34 xubuntu kernel: [    6.457548] [drm] nouveau 0000:02:00.0: BMP version 5.21
Aug 17 15:10:34 xubuntu kernel: [    6.457551] [drm] nouveau 0000:02:00.0: Bios version 04.1f.00.08
Aug 17 15:10:34 xubuntu kernel: [    6.457556] [drm] nouveau 0000:02:00.0: Found Display Configuration Block version 2.0
Aug 17 15:10:34 xubuntu kernel: [    6.457561] [drm] nouveau 0000:02:00.0: Raw DCB entry 0: 01000100 000088b8
Aug 17 15:10:34 xubuntu kernel: [    6.457565] [drm] nouveau 0000:02:00.0: Raw DCB entry 1: 02010210 000088b8
Aug 17 15:10:34 xubuntu kernel: [    6.457728] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 0 at offset 0x9E1E
Aug 17 15:10:34 xubuntu kernel: [    6.457755] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 1 at offset 0xA040
Aug 17 15:10:34 xubuntu kernel: [    6.457763] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 2 at offset 0x9E85
Aug 17 15:10:34 xubuntu kernel: [    6.472675] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 3 at offset 0xA192
Aug 17 15:10:34 xubuntu kernel: [    6.472684] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 4 at offset 0x9FDB
Aug 17 15:10:34 xubuntu kernel: [    6.472690] [drm] nouveau 0000:02:00.0: Unknown memclock table version 0.
Aug 17 15:10:34 xubuntu kernel: [    6.472953] firewire_ohci: Added fw-ohci device 0000:00:0d.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x0
Aug 17 15:10:34 xubuntu kernel: [    6.493106] [drm] nouveau 0000:02:00.0: 0 available performance level(s)
Aug 17 15:10:34 xubuntu kernel: [    6.493129] [drm] nouveau 0000:02:00.0: c: core 200MHz memory 167045M
Aug 17 15:10:34 xubuntu kernel: [    6.493388] [TTM] Zone  kernel: Available graphics memory: 443388 kiB.
Aug 17 15:10:34 xubuntu kernel: [    6.493392] [TTM] Zone highmem: Available graphics memory: 496608 kiB.
Aug 17 15:10:34 xubuntu kernel: [    6.493394] [TTM] Initializing pool allocator.
Aug 17 15:10:34 xubuntu kernel: [    6.493418] [drm] nouveau 0000:02:00.0: Detected 32MiB VRAM
Aug 17 15:10:34 xubuntu kernel: [    6.493642] agpgart-nvidia 0000:00:00.0: AGP 2.0 bridge
Aug 17 15:10:34 xubuntu kernel: [    6.493666] agpgart-nvidia 0000:00:00.0: putting AGP V2 device into 4x mode
Aug 17 15:10:34 xubuntu kernel: [    6.493730] nouveau 0000:02:00.0: putting AGP V2 device into 4x mode
Aug 17 15:10:34 xubuntu kernel: [    6.493735] [drm] nouveau 0000:02:00.0: 64 MiB GART (aperture)
Aug 17 15:10:34 xubuntu kernel: [    6.493824] [drm] nouveau 0000:02:00.0: Saving VGA fonts
Aug 17 15:10:34 xubuntu kernel: [    6.540410] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Aug 17 15:10:34 xubuntu kernel: [    6.540416] [drm] No driver support for vblank timestamp query.
Aug 17 15:10:34 xubuntu kernel: [    6.540424] [drm] nouveau 0000:02:00.0: Setting dpms mode 3 on vga encoder (output 0)
Aug 17 15:10:34 xubuntu kernel: [    6.540428] [drm] nouveau 0000:02:00.0: Setting dpms mode 3 on vga encoder (output 1)
Aug 17 15:10:34 xubuntu kernel: [    6.624075] [drm] nouveau 0000:02:00.0: Load detected on output B
Aug 17 15:10:34 xubuntu kernel: [    6.624345] [drm] nouveau 0000:02:00.0: allocated 1024x768 fb: 0x49000, bo f51df400
Aug 17 15:10:34 xubuntu kernel: [    6.624443] fbcon: nouveaufb (fb0) is primary device
Aug 17 15:10:34 xubuntu kernel: [    6.634546] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input4
Aug 17 15:10:34 xubuntu kernel: [    6.634857] generic-usb 0003:045E:0745.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:02.0-1/input0
Aug 17 15:10:34 xubuntu kernel: [    6.646008] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.1/input/input5
Aug 17 15:10:34 xubuntu kernel: [    6.646315] generic-usb 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:02.0-1/input1
Aug 17 15:10:34 xubuntu kernel: [    6.674172] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.2/input/input6
Aug 17 15:10:34 xubuntu kernel: [    6.674757] generic-usb 0003:045E:0745.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:02.0-1/input2
Aug 17 15:10:34 xubuntu kernel: [    6.674979] usbcore: registered new interface driver usbhid
Aug 17 15:10:34 xubuntu kernel: [    6.674981] usbhid: USB HID core driver
Aug 17 15:10:34 xubuntu kernel: [    7.333906] firewire_core: created device fw0: GUID 0000000000023f32, S400
Aug 17 15:10:34 xubuntu kernel: [    7.350885] [drm] nouveau 0000:02:00.0: Setting dpms mode 0 on vga encoder (output 1)
Aug 17 15:10:34 xubuntu kernel: [    7.350892] [drm] nouveau 0000:02:00.0: Output VGA-2 is running on CRTC 1 using output B
Aug 17 15:10:34 xubuntu kernel: [    7.351758] Console: switching to colour frame buffer device 128x48
Aug 17 15:10:34 xubuntu kernel: [    7.352578] fb0: nouveaufb frame buffer device
Aug 17 15:10:34 xubuntu kernel: [    7.352580] drm: registered panic notifier
Aug 17 15:10:34 xubuntu kernel: [    7.352600] [drm] Initialized nouveau 0.0.16 20090420 for 0000:02:00.0 on minor 0
Aug 17 15:10:34 xubuntu kernel: [    7.422443] scsi 4:0:0:0: Direct-Access     Kingston DT 101 G2        1.00 PQ: 0 ANSI: 2
Aug 17 15:10:34 xubuntu kernel: [    7.423142] sd 4:0:0:0: Attached scsi generic sg2 type 0
Aug 17 15:10:34 xubuntu kernel: [    7.423789] sd 4:0:0:0: [sdb] 7831552 512-byte logical blocks: (4.00 GB/3.73 GiB)
Aug 17 15:10:34 xubuntu kernel: [    7.424287] sd 4:0:0:0: [sdb] Write Protect is off
Aug 17 15:10:34 xubuntu kernel: [    7.424291] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
Aug 17 15:10:34 xubuntu kernel: [    7.424790] sd 4:0:0:0: [sdb] No Caching mode page present
Aug 17 15:10:34 xubuntu kernel: [    7.424794] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 17 15:10:34 xubuntu kernel: [    7.427415] sd 4:0:0:0: [sdb] No Caching mode page present
Aug 17 15:10:34 xubuntu kernel: [    7.427420] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 17 15:10:34 xubuntu kernel: [    7.428364]  sdb: sdb1
Aug 17 15:10:34 xubuntu kernel: [    7.430666] sd 4:0:0:0: [sdb] No Caching mode page present
Aug 17 15:10:34 xubuntu kernel: [    7.430672] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 17 15:10:34 xubuntu kernel: [    7.430677] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Aug 17 15:10:34 xubuntu kernel: [    7.536054] usb 3-1: new low-speed USB device number 2 using ohci_hcd
Aug 17 15:10:34 xubuntu kernel: [    7.762334] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input7
Aug 17 15:10:34 xubuntu kernel: [    7.765050] generic-usb 0003:046D:C508.0004: input,hidraw3: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.1-1/input0
Aug 17 15:10:34 xubuntu kernel: [    7.795214] Btrfs loaded
Aug 17 15:10:34 xubuntu kernel: [    7.805207] xor: automatically using best checksumming function: pIII_sse
Aug 17 15:10:34 xubuntu kernel: [    7.824019]    pIII_sse  :  2688.000 MB/sec
Aug 17 15:10:34 xubuntu kernel: [    7.824023] xor: using function: pIII_sse (2688.000 MB/sec)
Aug 17 15:10:34 xubuntu kernel: [    7.825654] device-mapper: dm-raid45: initialized v0.2594b
Aug 17 15:10:34 xubuntu kernel: [    8.209069] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 17 15:10:34 xubuntu kernel: [    8.431079] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Aug 17 15:10:34 xubuntu kernel: [   10.018290] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Aug 17 15:10:34 xubuntu kernel: [   22.996129] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 17 15:10:34 xubuntu kernel: [   23.129434] Adding 1013756k swap on /dev/sda5.  Priority:-1 extents:1 across:1013756k 
Aug 17 15:10:34 xubuntu kernel: [   23.702810] lp: driver loaded but no devices found
Aug 17 15:10:34 xubuntu kernel: [   23.706630] Bluetooth: Core ver 2.16
Aug 17 15:10:34 xubuntu kernel: [   23.711882] NET: Registered protocol family 31
Aug 17 15:10:34 xubuntu kernel: [   23.711889] Bluetooth: HCI device and connection manager initialized
Aug 17 15:10:34 xubuntu kernel: [   23.711893] Bluetooth: HCI socket layer initialized
Aug 17 15:10:34 xubuntu kernel: [   23.711896] Bluetooth: L2CAP socket layer initialized
Aug 17 15:10:34 xubuntu kernel: [   23.711910] Bluetooth: SCO socket layer initialized
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin AnyData
Aug 17 15:10:34 xubuntu bluetoothd[1315]: Starting SDP server
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin Generic
Aug 17 15:10:34 xubuntu bluetoothd[1315]: Failed to init alert plugin
Aug 17 15:10:34 xubuntu bluetoothd[1315]: Failed to init time plugin
Aug 17 15:10:34 xubuntu bluetoothd[1315]: Failed to init proximity plugin
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin Gobi
Aug 17 15:10:34 xubuntu avahi-daemon[1340]: Successfully called chroot().
Aug 17 15:10:34 xubuntu avahi-daemon[1340]: Successfully dropped remaining capabilities.
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin Option High-Speed
Aug 17 15:10:34 xubuntu kernel: [   23.765676] Bluetooth: RFCOMM TTY layer initialized
Aug 17 15:10:34 xubuntu kernel: [   23.765694] Bluetooth: RFCOMM socket layer initialized
Aug 17 15:10:34 xubuntu kernel: [   23.765697] Bluetooth: RFCOMM ver 1.11
Aug 17 15:10:34 xubuntu kernel: [   23.769982] ppdev: user-space parallel port driver
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin Huawei
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin Linktop
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin Longcheer
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin Ericsson MBM
Aug 17 15:10:34 xubuntu avahi-daemon[1340]: Loading service file /services/udisks.service.
Aug 17 15:10:34 xubuntu avahi-daemon[1340]: Network interface enumeration completed.
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin MotoC
Aug 17 15:10:34 xubuntu avahi-daemon[1340]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 17 15:10:34 xubuntu kernel: [   23.812273] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 17 15:10:34 xubuntu kernel: [   23.812278] Bluetooth: BNEP filters: protocol multicast
Aug 17 15:10:34 xubuntu kernel: [   23.814129] parport_pc 00:0b: reported by Plug and Play ACPI
Aug 17 15:10:34 xubuntu kernel: [   23.814192] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Aug 17 15:10:34 xubuntu avahi-daemon[1340]: Server startup complete. Host name is xubuntu.local. Local service cookie is 827774896.
Aug 17 15:10:34 xubuntu avahi-daemon[1340]: Service "xubuntu" (/services/udisks.service) successfully established.
Aug 17 15:10:34 xubuntu bluetoothd[1315]: Failed to init gatt_example plugin
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> NetworkManager (version 0.9.4.0) is starting...
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin Nokia
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin Novatel
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin Option
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin Samsung
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin Sierra
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin SimTech
Aug 17 15:10:34 xubuntu kernel: [   23.908403] lp0: using parport0 (interrupt-driven).
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin Wavecom
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin X22X
Aug 17 15:10:34 xubuntu modem-manager[1306]: <info>  Loaded plugin ZTE
Aug 17 15:10:34 xubuntu kernel: [   23.974739] i2c i2c-3: nForce2 SMBus adapter at 0x5000
Aug 17 15:10:34 xubuntu kernel: [   23.977731] i2c i2c-4: nForce2 SMBus adapter at 0x5100
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> DNS: loaded plugin dnsmasq
Aug 17 15:10:34 xubuntu dbus[1284]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Aug 17 15:10:34 xubuntu polkitd[1424]: started daemon version 0.104 using authority implementation `local' version `0.104'
Aug 17 15:10:34 xubuntu dbus[1284]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Aug 17 15:10:34 xubuntu NetworkManager[1371]:    SCPlugin-Ifupdown: init!
Aug 17 15:10:34 xubuntu NetworkManager[1371]:    SCPlugin-Ifupdown: update_system_hostname
Aug 17 15:10:34 xubuntu NetworkManager[1371]:    SCPluginIfupdown: management mode: unmanaged
Aug 17 15:10:34 xubuntu NetworkManager[1371]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/net/eth0, iface: eth0)
Aug 17 15:10:34 xubuntu NetworkManager[1371]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 17 15:10:34 xubuntu NetworkManager[1371]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 17 15:10:34 xubuntu NetworkManager[1371]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 17 15:10:34 xubuntu NetworkManager[1371]:    SCPlugin-Ifupdown: end _init.
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 17 15:10:34 xubuntu NetworkManager[1371]:    Ifupdown: get unmanaged devices count: 0
Aug 17 15:10:34 xubuntu NetworkManager[1371]:    SCPlugin-Ifupdown: (146255440) ... get_connections.
Aug 17 15:10:34 xubuntu NetworkManager[1371]:    SCPlugin-Ifupdown: (146255440) ... get_connections (managed=false): return empty list.
Aug 17 15:10:34 xubuntu NetworkManager[1371]:    Ifupdown: get unmanaged devices count: 0
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> modem-manager is now available
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Networking is enabled by state file
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <warn> failed to allocate link cache: (-10) Operation not supported
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> (eth0): carrier is OFF
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> (eth0): now managed
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> (eth0): bringing up device.
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> (eth0): carrier now ON (device state 20)
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> (eth0): preparing device.
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> (eth0): deactivating device (reason 'managed') [2]
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:04.0/net/eth0
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> (eth0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Auto-activating connection 'Wired connection 1'.
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Activation (eth0) starting connection 'Wired connection 1'
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> dhclient started with pid 1475
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Activation (eth0) Beginning IP6 addrconf.
Aug 17 15:10:34 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Aug 17 15:10:35 xubuntu dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Aug 17 15:10:35 xubuntu dhclient: Copyright 2004-2011 Internet Systems Consortium.
Aug 17 15:10:35 xubuntu dhclient: All rights reserved.
Aug 17 15:10:35 xubuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Aug 17 15:10:35 xubuntu dhclient: 
Aug 17 15:10:35 xubuntu NetworkManager[1371]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Aug 17 15:10:35 xubuntu dhclient: Listening on LPF/eth0/00:e0:4c:b9:b7:6a
Aug 17 15:10:35 xubuntu dhclient: Sending on   LPF/eth0/00:e0:4c:b9:b7:6a
Aug 17 15:10:35 xubuntu dhclient: Sending on   Socket/fallback
Aug 17 15:10:35 xubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Aug 17 15:10:35 xubuntu dhclient: DHCPREQUEST of 192.168.0.100 on eth0 to 255.255.255.255 port 67
Aug 17 15:10:35 xubuntu dhclient: DHCPOFFER of 192.168.0.100 from 192.168.0.1
Aug 17 15:10:35 xubuntu dhclient: DHCPACK of 192.168.0.100 from 192.168.0.1
Aug 17 15:10:35 xubuntu kernel: [   24.703809] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 17 15:10:35 xubuntu NetworkManager[1371]: <info> (eth0): DHCPv4 state changed preinit -> bound
Aug 17 15:10:35 xubuntu NetworkManager[1371]: <info>   address 192.168.0.100
Aug 17 15:10:35 xubuntu NetworkManager[1371]: <info>   prefix 24 (255.255.255.0)
Aug 17 15:10:35 xubuntu NetworkManager[1371]: <info>   gateway 192.168.0.1
Aug 17 15:10:35 xubuntu NetworkManager[1371]: <info>   nameserver '192.168.0.1'
Aug 17 15:10:35 xubuntu NetworkManager[1371]: <info>   domain name 'cable.virginmedia.net'
Aug 17 15:10:35 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Aug 17 15:10:35 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Aug 17 15:10:35 xubuntu avahi-daemon[1340]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.100.
Aug 17 15:10:35 xubuntu avahi-daemon[1340]: New relevant interface eth0.IPv4 for mDNS.
Aug 17 15:10:35 xubuntu avahi-daemon[1340]: Registering new address record for 192.168.0.100 on eth0.IPv4.
Aug 17 15:10:35 xubuntu dhclient: bound to 192.168.0.100 -- renewal in 265053 seconds.
Aug 17 15:10:35 xubuntu kernel: [   24.812079] device-mapper: multipath: version 1.3.0 loaded
Aug 17 15:10:35 xubuntu kernel: [   25.020559] psmouse serio1: hgpk: ID: 10 00 64
Aug 17 15:10:35 xubuntu kernel: [   25.311002] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input8
Aug 17 15:10:35 xubuntu failsafe: Failsafe of 120 seconds reached.
Aug 17 15:10:36 xubuntu NetworkManager[1371]: <info> DNS: starting dnsmasq...
Aug 17 15:10:36 xubuntu NetworkManager[1371]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Aug 17 15:10:36 xubuntu kernel: [   25.794567] init: failsafe main process (1603) killed by TERM signal
Aug 17 15:10:36 xubuntu dnsmasq[1658]: started, version 2.59 cache disabled
Aug 17 15:10:36 xubuntu dnsmasq[1658]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Aug 17 15:10:36 xubuntu dnsmasq[1658]: using nameserver 192.168.0.1#53
Aug 17 15:10:36 xubuntu acpid: starting up with proc fs
Aug 17 15:10:36 xubuntu acpid: 35 rules loaded
Aug 17 15:10:36 xubuntu cron[1748]: (CRON) INFO (pidfile fd = 3)
Aug 17 15:10:36 xubuntu cron[1849]: (CRON) STARTUP (fork ok)
Aug 17 15:10:36 xubuntu cron[1849]: (CRON) INFO (Running @reboot jobs)
Aug 17 15:10:36 xubuntu acpid: waiting for events: event logging is off
Aug 17 15:10:37 xubuntu udev-configure-printer: add /module/lp
Aug 17 15:10:37 xubuntu udev-configure-printer: Failed to get parent
Aug 17 15:10:37 xubuntu avahi-daemon[1340]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::2e0:4cff:feb9:b76a.
Aug 17 15:10:37 xubuntu avahi-daemon[1340]: New relevant interface eth0.IPv6 for mDNS.
Aug 17 15:10:37 xubuntu avahi-daemon[1340]: Registering new address record for fe80::2e0:4cff:feb9:b76a on eth0.*.
Aug 17 15:10:37 xubuntu udev-configure-printer: add /devices/pnp0/00:0b/printer/lp0
Aug 17 15:10:37 xubuntu udev-configure-printer: Failed to get parent
Aug 17 15:10:37 xubuntu NetworkManager[1371]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Aug 17 15:10:37 xubuntu NetworkManager[1371]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Aug 17 15:10:37 xubuntu NetworkManager[1371]: <info> Activation (eth0) successful, device activated.
Aug 17 15:10:37 xubuntu dbus[1284]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Aug 17 15:10:37 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Aug 17 15:10:37 xubuntu NetworkManager[1371]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/net/eth0, iface: eth0)
Aug 17 15:10:37 xubuntu NetworkManager[1371]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 17 15:10:37 xubuntu NetworkManager[1371]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 17 15:10:37 xubuntu NetworkManager[1371]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 17 15:10:37 xubuntu dbus[1284]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 17 15:10:37 xubuntu kernel: [   27.192499] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
Aug 17 15:10:37 xubuntu kernel: [   27.192510] snd_intel8x0 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 20 (level, high) -> IRQ 20
Aug 17 15:10:37 xubuntu kernel: [   27.192550] snd_intel8x0 0000:00:06.0: setting latency timer to 64
Aug 17 15:10:37 xubuntu kernel: [   27.612070] intel8x0_measure_ac97_clock: measured 52702 usecs (2560 samples)
Aug 17 15:10:37 xubuntu kernel: [   27.612076] intel8x0: clocking to 47431
Aug 17 15:10:38 xubuntu dbus[1284]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Aug 17 15:10:38 xubuntu dbus[1284]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Aug 17 15:10:44 xubuntu acpid: client connected from 3152[0:0]
Aug 17 15:10:44 xubuntu acpid: 1 client rule loaded
Aug 17 15:10:45 xubuntu kernel: [   34.668056] [drm] nouveau 0000:02:00.0: Load detected on output B
Aug 17 15:10:45 xubuntu kernel: [   34.784058] [drm] nouveau 0000:02:00.0: Load detected on output B
Aug 17 15:10:45 xubuntu kernel: [   34.942349] [drm] nouveau 0000:02:00.0: Setting dpms mode 3 on vga encoder (output 1)
Aug 17 15:10:45 xubuntu kernel: [   35.613138] [drm] nouveau 0000:02:00.0: Setting dpms mode 0 on vga encoder (output 1)
Aug 17 15:10:45 xubuntu kernel: [   35.613144] [drm] nouveau 0000:02:00.0: Output VGA-2 is running on CRTC 1 using output B
Aug 17 15:10:46 xubuntu kernel: [   35.832036] eth0: no IPv6 routers present
Aug 17 15:10:47 xubuntu ntpdate[2220]: adjust time server 91.189.94.4 offset -0.157838 sec
Aug 17 15:10:47 xubuntu dbus[1284]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Aug 17 15:10:47 xubuntu dbus[1284]: [system] Successfully activated service 'org.freedesktop.UDisks'
Aug 17 15:10:51 xubuntu ubiquity[3259]: Ubiquity 2.10.16
Aug 17 15:10:55 xubuntu NetworkManager[1371]: <info> (eth0): IP6 addrconf timed out or failed.
Aug 17 15:10:55 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Aug 17 15:10:55 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Aug 17 15:10:55 xubuntu NetworkManager[1371]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Aug 17 15:10:55 xubuntu ubiquity[3259]: log-output -t ubiquity laptop-detect
Aug 17 15:10:56 xubuntu dbus[1284]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Aug 17 15:10:56 xubuntu dbus[1284]: [system] Successfully activated service 'org.freedesktop.Accounts'
Aug 17 15:10:56 xubuntu accounts-daemon[3294]: started daemon version 0.6.15
Aug 17 15:10:56 xubuntu ubiquity[3259]: log-output -t ubiquity fontconfig-voodoo --auto --force --quiet
Aug 17 15:10:57 xubuntu ubiquity[3259]: log-output -t ubiquity laptop-detect
Aug 17 15:11:01 xubuntu ubiquity[3259]: switched to page language
Aug 17 15:11:03 xubuntu ubiquity[3259]: switched to page language
Aug 17 15:11:21 xubuntu localechooser: info: Language = 'en'
Aug 17 15:11:21 xubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Aug 17 15:11:21 xubuntu localechooser: info: Set debian-installer/language = 'en'
Aug 17 15:11:21 xubuntu localechooser: info: Default country = 'US'
Aug 17 15:11:21 xubuntu localechooser: info: Default locale = 'en_US.UTF-8'
Aug 17 15:11:21 xubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Aug 17 15:11:21 xubuntu localechooser: info: Set debian-installer/country = 'US'
Aug 17 15:11:21 xubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Aug 17 15:11:21 xubuntu localechooser: info: System locale (debian-installer/locale) = 'en_US.UTF-8'
Aug 17 15:11:23 xubuntu ubiquity[3259]: debconffilter_done: ubi-language (current: ubi-language)
Aug 17 15:11:23 xubuntu ubiquity[3259]: Step_before = stepLanguage
Aug 17 15:11:24 xubuntu ubiquity[3259]: switched to page prepare
Aug 17 15:11:39 xubuntu kernel: [   88.755647] ondemand governor failed, too long transition latency of HW, fallback to performance governor
Aug 17 15:11:43 xubuntu ubiquity[3259]: debconffilter_done: ubi-prepare (current: ubi-prepare)
Aug 17 15:11:43 xubuntu ubiquity[3259]: Step_before = stepPrepare
Aug 17 15:11:43 xubuntu ubiquity[3259]: Step_before = stepPrepare
Aug 17 15:11:43 xubuntu activate-dmraid: No Serial ATA RAID disks detected
Aug 17 15:11:44 xubuntu kernel: [   93.686681] JFS: nTxBlock = 7759, nTxLock = 62076
Aug 17 15:11:44 xubuntu kernel: [   93.820399] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Aug 17 15:11:44 xubuntu kernel: [   93.826981] SGI XFS Quota Management subsystem
Aug 17 15:11:45 xubuntu kernel: [   95.233536] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 17 15:11:46 xubuntu kernel: [   95.630478] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Aug 17 15:11:46 xubuntu ubiquity: umount: /tmp/tmp.XqEyvcCvef: not mounted
Aug 17 15:11:46 xubuntu ubiquity: 
Aug 17 15:11:46 xubuntu kernel: [   95.891818] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 17 15:11:46 xubuntu kernel: [   96.130418] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Aug 17 15:11:46 xubuntu ubiquity: umount: /tmp/tmp.PvcuF88m0m: not mounted
Aug 17 15:11:46 xubuntu ubiquity: 
Aug 17 15:11:47 xubuntu kernel: [   96.758426] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 17 15:11:47 xubuntu kernel: [   96.975150] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Aug 17 15:11:47 xubuntu ubiquity: umount: /tmp/tmp.e4nDrJgKOE: not mounted
Aug 17 15:11:47 xubuntu ubiquity: 
Aug 17 15:11:47 xubuntu kernel: [   97.236265] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 17 15:11:47 xubuntu kernel: [   97.488646] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Aug 17 15:11:47 xubuntu ubiquity: umount: /tmp/tmp.6PCj8P9blS: not mounted
Aug 17 15:11:47 xubuntu ubiquity: 
Aug 17 15:11:48 xubuntu kernel: [   97.941671] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 17 15:11:48 xubuntu kernel: [   98.188632] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Aug 17 15:11:48 xubuntu ubiquity: umount: /tmp/tmp.IalzTdWkKv: not mounted
Aug 17 15:11:48 xubuntu ubiquity: 
Aug 17 15:11:48 xubuntu kernel: [   98.449965] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 17 15:11:49 xubuntu kernel: [   98.696919] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Aug 17 15:11:49 xubuntu ubiquity: umount: /tmp/tmp.wDdRfFbTY3: not mounted
Aug 17 15:11:49 xubuntu ubiquity: 
Aug 17 15:11:49 xubuntu kernel: [   98.942670] NTFS driver 2.1.30 [Flags: R/O MODULE].
Aug 17 15:11:49 xubuntu kernel: [   98.982057] QNX4 filesystem 0.2.3 registered.
Aug 17 15:11:49 xubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Aug 17 15:11:49 xubuntu 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
Aug 17 15:11:49 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Aug 17 15:11:49 xubuntu 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Aug 17 15:11:49 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Aug 17 15:11:49 xubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Aug 17 15:11:49 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Aug 17 15:11:49 xubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Aug 17 15:11:49 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Aug 17 15:11:49 xubuntu 20microsoft: debug: /dev/sda1 is not a MS partition: exiting
Aug 17 15:11:49 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Aug 17 15:11:49 xubuntu 30utility: debug: /dev/sda1 is not a FAT partition: exiting
Aug 17 15:11:49 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Aug 17 15:11:50 xubuntu 40lsb: result: /dev/sda1:Ubuntu 12.04 LTS (12.04):Ubuntu:linux
Aug 17 15:11:50 xubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/40lsb
Aug 17 15:11:50 xubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 17 15:11:50 xubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Aug 17 15:11:50 xubuntu 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Aug 17 15:11:50 xubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 17 15:11:50 xubuntu os-prober: debug: /dev/sda5: is active swap
Aug 17 15:11:50 xubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda6
Aug 17 15:11:50 xubuntu 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
Aug 17 15:11:50 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Aug 17 15:11:50 xubuntu 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
Aug 17 15:11:50 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Aug 17 15:11:50 xubuntu 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
Aug 17 15:11:50 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Aug 17 15:11:50 xubuntu macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
Aug 17 15:11:50 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Aug 17 15:11:50 xubuntu 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
Aug 17 15:11:50 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Aug 17 15:11:50 xubuntu 30utility: debug: /dev/sda6 is not a FAT partition: exiting
Aug 17 15:11:50 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Aug 17 15:11:50 xubuntu 40lsb: result: /dev/sda6:Ubuntu 12.04 LTS (12.04):Ubuntu1:linux
Aug 17 15:11:50 xubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/40lsb
Aug 17 15:11:50 xubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 17 15:11:50 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb1
Aug 17 15:11:50 xubuntu 10freedos: debug: /dev/sdb1 is a FAT32 partition
Aug 17 15:11:50 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb1
Aug 17 15:11:50 xubuntu 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Aug 17 15:11:50 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb1
Aug 17 15:11:50 xubuntu macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Aug 17 15:11:50 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb1
Aug 17 15:11:50 xubuntu 20microsoft: debug: /dev/sdb1 is a FAT32 partition
Aug 17 15:11:50 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
Aug 17 15:11:50 xubuntu 30utility: debug: /dev/sdb1 is a FAT32 partition
Aug 17 15:11:50 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
Aug 17 15:11:50 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
Aug 17 15:11:50 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
Aug 17 15:11:50 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sdb1
Aug 17 15:11:50 xubuntu 83haiku: debug: /dev/sdb1 is not a BeFS partition: exiting
Aug 17 15:11:50 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90bsd-distro on mounted /dev/sdb1
Aug 17 15:11:50 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
Aug 17 15:11:50 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
Aug 17 15:11:50 xubuntu ubiquity[3259]: switched to page partman
Aug 17 15:11:59 xubuntu ubiquity[3259]: switched to page partman
Aug 17 15:12:14 xubuntu ubiquity[3259]: debconffilter_done: ubi-partman (current: ubi-partman)
Aug 17 15:12:14 xubuntu ubiquity[3259]: Step_before = stepPartAuto
Aug 17 15:12:14 xubuntu clock-setup: Fri Aug 17 15:12:14 UTC 2012
Aug 17 15:12:14 xubuntu clock-setup: rdate: adjust local clock by -0.103601 seconds
Aug 17 15:12:16 xubuntu ubiquity[3259]: switched to page timezone
Aug 17 15:12:16 xubuntu kernel: [  126.393666] Adding 1013756k swap on /dev/sda5.  Priority:-1 extents:1 across:1013756k 
Aug 17 15:12:16 xubuntu partman: mke2fs 1.42 (29-Nov-2011)
Aug 17 15:12:21 xubuntu kernel: [  131.671056] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Aug 17 15:12:22 xubuntu ubiquity[3259]: debconffilter_done: ubiquity.components.partman_commit (current: ubi-timezone)
Aug 17 15:12:22 xubuntu install.py: keeping packages due to preseeding: 
Aug 17 15:12:22 xubuntu install.py: keeping language packs for: en_US.UTF-8
Aug 17 15:12:24 xubuntu localechooser: info: debian-installer/language preseeded to 'en' (seen: false)
Aug 17 15:12:24 xubuntu localechooser: info: debian-installer/country preseeded to 'GB' (seen: true)
Aug 17 15:12:24 xubuntu localechooser: info: debian-installer/locale preseeded to 'en_GB.UTF-8' (seen: true)
Aug 17 15:12:24 xubuntu localechooser: info: Preseeded language ignored: unknown language code
Aug 17 15:12:24 xubuntu localechooser: info: Language = 'en'
Aug 17 15:12:24 xubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Aug 17 15:12:24 xubuntu localechooser: info: Set debian-installer/language = 'en'
Aug 17 15:12:24 xubuntu localechooser: info: Default country = 'US'
Aug 17 15:12:24 xubuntu localechooser: info: Default locale = 'en_US.UTF-8'
Aug 17 15:12:24 xubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Aug 17 15:12:24 xubuntu localechooser: info: Set debian-installer/country = 'GB'
Aug 17 15:12:25 xubuntu localechooser: info: Set debian-installer/locale = 'en_GB.UTF-8'
Aug 17 15:12:25 xubuntu localechooser: info: System locale (debian-installer/locale) = 'en_GB.UTF-8'
Aug 17 15:12:25 xubuntu localechooser: info: Set debian-installer/language = 'en_GB:en'
Aug 17 15:12:25 xubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Aug 17 15:12:25 xubuntu 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Aug 17 15:12:25 xubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 17 15:12:25 xubuntu os-prober: debug: /dev/sda5: is active swap
Aug 17 15:12:25 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb1
Aug 17 15:12:25 xubuntu 10freedos: debug: /dev/sdb1 is a FAT32 partition
Aug 17 15:12:25 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb1
Aug 17 15:12:25 xubuntu 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Aug 17 15:12:25 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb1
Aug 17 15:12:25 xubuntu macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Aug 17 15:12:25 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb1
Aug 17 15:12:25 xubuntu 20microsoft: debug: /dev/sdb1 is a FAT32 partition
Aug 17 15:12:25 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
Aug 17 15:12:25 xubuntu 30utility: debug: /dev/sdb1 is a FAT32 partition
Aug 17 15:12:25 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
Aug 17 15:12:25 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
Aug 17 15:12:25 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
Aug 17 15:12:25 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sdb1
Aug 17 15:12:25 xubuntu 83haiku: debug: /dev/sdb1 is not a BeFS partition: exiting
Aug 17 15:12:25 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90bsd-distro on mounted /dev/sdb1
Aug 17 15:12:25 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
Aug 17 15:12:25 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
Aug 17 15:12:25 xubuntu ubiquity[3259]: debconffilter_done: ubi-timezone (current: ubi-timezone)
Aug 17 15:12:25 xubuntu ubiquity[3259]: Step_before = stepLocation
Aug 17 15:12:27 xubuntu ubiquity[3259]: switched to page console_setup
Aug 17 15:12:28 xubuntu ubiquity[3259]: log-output -t ubiquity setxkbmap -model pc105 -layout gb -option  -option lv3:ralt_switch
Aug 17 15:12:43 xubuntu ubiquity: Your console font configuration will be updated the next time your system
Aug 17 15:12:44 xubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Aug 17 15:12:44 xubuntu ubiquity[3259]: log-output -t ubiquity setxkbmap -model pc105 -layout gb -option 
Aug 17 15:12:44 xubuntu ubiquity[3259]: debconffilter_done: ubi-console-setup (current: ubi-console-setup)
Aug 17 15:12:44 xubuntu ubiquity[3259]: Step_before = stepKeyboardConf
Aug 17 15:12:44 xubuntu ubiquity[3259]: switched to page usersetup
Aug 17 15:13:35 xubuntu ubiquity[3259]: debconffilter_done: ubi-usersetup (current: ubi-usersetup)
Aug 17 15:13:35 xubuntu ubiquity[3259]: Step_before = stepUserInfo
Aug 17 15:13:36 xubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Aug 17 15:13:36 xubuntu 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Aug 17 15:13:36 xubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 17 15:13:36 xubuntu os-prober: debug: /dev/sda5: is active swap
Aug 17 15:13:36 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb1
Aug 17 15:13:36 xubuntu 10freedos: debug: /dev/sdb1 is a FAT32 partition
Aug 17 15:13:36 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb1
Aug 17 15:13:36 xubuntu 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Aug 17 15:13:36 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb1
Aug 17 15:13:36 xubuntu macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Aug 17 15:13:36 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb1
Aug 17 15:13:36 xubuntu 20microsoft: debug: /dev/sdb1 is a FAT32 partition
Aug 17 15:13:36 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
Aug 17 15:13:36 xubuntu 30utility: debug: /dev/sdb1 is a FAT32 partition
Aug 17 15:13:36 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
Aug 17 15:13:36 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
Aug 17 15:13:36 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
Aug 17 15:13:36 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sdb1
Aug 17 15:13:37 xubuntu 83haiku: debug: /dev/sdb1 is not a BeFS partition: exiting
Aug 17 15:13:37 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90bsd-distro on mounted /dev/sdb1
Aug 17 15:13:37 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
Aug 17 15:13:37 xubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
Aug 17 15:13:37 xubuntu ubiquity[3259]: debconffilter_done: ubi-migrationassistant (current: ubi-migrationassistant)
Aug 17 15:13:37 xubuntu ubiquity[3259]: Step_before = stepUserInfo
Aug 17 15:14:59 xubuntu ubiquity[3259]: debconffilter_done: ubiquity.components.install (current: None)
Aug 17 15:15:10 xubuntu kernel: [  300.008029] [Hardware Error]: Machine check events logged
Aug 17 15:15:11 xubuntu plugininstall.py: log-output -t ubiquity chroot /target python2.7 /usr/lib/python2.7/py_compile.py /usr/lib/python2.7/__future__.py /usr/lib/python2.7/_abcoll.py /usr/lib/python2.7/_weakrefset.py /usr/lib/python2.7/abc.py /usr/lib/python2.7/atexit.py /usr/lib/python2.7/ConfigParser.py /usr/lib/python2.7/StringIO.py /usr/lib/python2.7/UserDict.py /usr/lib/python2.7/base64.py /usr/lib/python2.7/bisect.py /usr/lib/python2.7/codecs.py /usr/lib/python2.7/collections.py /usr/lib/python2.7/compileall.py /usr/lib/python2.7/copy.py /usr/lib/python2.7/copy_reg.py /usr/lib/python2.7/dis.py /usr/lib/python2.7/fnmatch.py /usr/lib/python2.7/functools.py /usr/lib/python2.7/genericpath.py /usr/lib/python2.7/getopt.py /usr/lib/python2.7/glob.py /usr/lib/python2.7/hashlib.py /usr/lib/python2.7/heapq.py /usr/lib/python2.7/inspect.py /usr/lib/python2.7/keyword.py /usr/lib/python2.7/linecache.py /usr/lib/python2.7/md5.py /usr/lib/python2.7/opcode.py /usr/lib/python2.7/optparse.py /usr/lib/python2.7/os.py /usr/lib/python2.7/pickle.py /usr/lib/python2.7/platform.py /usr/lib/python2.7/popen2.py /usr/lib/python2.7/posixpath.py /usr/lib/python2.7/pkgutil.py /usr/lib/python2.7/py_compile.py /usr/lib/python2.7/random.py /usr/lib/python2.7/re.py /usr/lib/python2.7/repr.py /usr/lib/python2.7/runpy.py /usr/lib/python2.7/sha.py /usr/lib/python2.7/shutil.py /usr/lib/python2.7/socket.py /usr/lib/python2.7/sre.py /usr/lib/python2.7/sre_compile.py /usr/lib/python2.7/sre_constants.py /usr/lib/python2.7/sre_parse.py /usr/lib/python2.7/ssl.py /usr/lib/python2.7/stat.py /usr/lib/python2.7/string.py /usr/lib/python2.7/struct.py /usr/lib/python2.7/subprocess.py /usr/lib/python2.7/sysconfig.py /usr/lib/python2.7/tempfile.py /usr/lib/python2.7/textwrap.py /usr/lib/python2.7/token.py /usr/lib/python2.7/tokenize.py /usr/lib/python2.7/traceback.py /usr/lib/python2.7/types.py /usr/lib/python2.7/weakref.py /usr/lib/python2.7/warnings.py /usr/lib/python2.7/logging/__init__.py /usr/lib/python2.7/logging/config.py /usr/lib/python2.7/logging/han
Aug 17 15:15:14 xubuntu plugininstall.py: log-output -t ubiquity chroot /target python2.7 /usr/lib/python2.7/py_compile.py /usr/lib/python2.7/test/regrtest.py /usr/lib/python2.7/test/test_support.py /usr/lib/python2.7/test/__init__.py /usr/lib/python2.7/test/pystone.py /usr/lib/python2.7/lib-tk/Canvas.py /usr/lib/python2.7/lib-tk/Dialog.py /usr/lib/python2.7/lib-tk/FileDialog.py /usr/lib/python2.7/lib-tk/FixTk.py /usr/lib/python2.7/lib-tk/ScrolledText.py /usr/lib/python2.7/lib-tk/SimpleDialog.py /usr/lib/python2.7/lib-tk/Tix.py /usr/lib/python2.7/lib-tk/Tkconstants.py /usr/lib/python2.7/lib-tk/Tkdnd.py /usr/lib/python2.7/lib-tk/Tkinter.py /usr/lib/python2.7/lib-tk/tkColorChooser.py /usr/lib/python2.7/lib-tk/tkCommonDialog.py /usr/lib/python2.7/lib-tk/tkFileDialog.py /usr/lib/python2.7/lib-tk/tkFont.py /usr/lib/python2.7/lib-tk/tkMessageBox.py /usr/lib/python2.7/lib-tk/tkSimpleDialog.py /usr/lib/python2.7/lib-tk/ttk.py /usr/lib/python2.7/lib-tk/turtle.py /usr/lib/python2.7/encodings/big5.py /usr/lib/python2.7/encodings/big5hkscs.py /usr/lib/python2.7/encodings/bz2_codec.py /usr/lib/python2.7/encodings/cp932.py /usr/lib/python2.7/encodings/cp949.py /usr/lib/python2.7/encodings/cp950.py /usr/lib/python2.7/encodings/euc_jis_2004.py /usr/lib/python2.7/encodings/euc_jisx0213.py /usr/lib/python2.7/encodings/euc_jp.py /usr/lib/python2.7/encodings/euc_kr.py /usr/lib/python2.7/encodings/gb18030.py /usr/lib/python2.7/encodings/gb2312.py /usr/lib/python2.7/encodings/gbk.py /usr/lib/python2.7/encodings/iso2022_jp.py /usr/lib/python2.7/encodings/iso2022_jp_1.py /usr/lib/python2.7/encodings/iso2022_jp_2.py /usr/lib/python2.7/encodings/iso2022_jp_2004.py /usr/lib/python2.7/encodings/iso2022_jp_3.py /usr/lib/python2.7/encodings/iso2022_jp_ext.py /usr/lib/python2.7/encodings/iso2022_kr.py /usr/lib/python2.7/encodings/johab.py /usr/lib/python2.7/encodings/shift_jis.py /usr/lib/python2.7/encodings/shift_jis_2004.py /usr/lib/python2.7/encodings/shift_jisx0213.py /usr/lib/python2.7/compiler/__init__.py /usr/lib/python2.7/compiler/ast.py /
Aug 17 15:15:15 xubuntu ubiquity: Listing /usr/share/python/ ...
Aug 17 15:15:15 xubuntu ubiquity: Listing /usr/share/python/debpython ...
Aug 17 15:15:15 xubuntu ubiquity: Compiling /usr/share/python/debpython/__init__.py ...
Aug 17 15:15:15 xubuntu ubiquity: Compiling /usr/share/python/debpython/debhelper.py ...
Aug 17 15:15:15 xubuntu ubiquity: Compiling /usr/share/python/debpython/depends.py ...
Aug 17 15:15:15 xubuntu ubiquity: Compiling /usr/share/python/debpython/files.py ...
Aug 17 15:15:15 xubuntu ubiquity: Compiling /usr/share/python/debpython/namespace.py ...
Aug 17 15:15:15 xubuntu ubiquity: Compiling /usr/share/python/debpython/option.py ...
Aug 17 15:15:15 xubuntu ubiquity: Compiling /usr/share/python/debpython/pydist.py ...
Aug 17 15:15:15 xubuntu ubiquity: Compiling /usr/share/python/debpython/tools.py ...
Aug 17 15:15:15 xubuntu ubiquity: Compiling /usr/share/python/debpython/version.py ...
Aug 17 15:15:15 xubuntu ubiquity: Listing /usr/share/python/ns ...
Aug 17 15:15:15 xubuntu ubiquity: Compiling /usr/share/python/pyversions.py ...
Aug 17 15:15:15 xubuntu ubiquity: Listing /usr/share/python/runtime.d ...
Aug 17 15:15:15 xubuntu plugininstall.py: log-output -t ubiquity chroot /target python2.7 -m compileall /usr/share/python/
Aug 17 15:15:15 xubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Aug 17 15:15:15 xubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Aug 17 15:15:15 xubuntu plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/public_modules.rtinstall rtinstall python2.7  2.7.3-0ubuntu3
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ibus-pinyin.rtupdate pre-rtupdate python2.7 python2.7
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/alacarte.rtupdate pre-rtupdate python2.7 python2.7
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/catfish.rtupdate pre-rtupdate python2.7 python2.7
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/onboard.rtupdate pre-rtupdate python2.7 python2.7
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ibus.rtupdate pre-rtupdate python2.7 python2.7
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ubiquity-frontend-gtk.rtupdate pre-rtupdate python2.7 python2.7
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/launchpad-integration.rtupdate pre-rtupdate python2.7 python2.7
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/gimp.rtupdate pre-rtupdate python2.7 python2.7
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ibus-table.rtupdate pre-rtupdate python2.7 python2.7
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/software-center.rtupdate pre-rtupdate python2.7 python2.7
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/apport.rtupdate pre-rtupdate python2.7 python2.7
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/apt-xapian-index.rtupdate pre-rtupdate python2.7 python2.7
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/hplip-data.rtupdate pre-rtupdate python2.7 python2.7
Aug 17 15:15:30 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ubiquity.rtupdate pre-rtupdate python2.7 python2.7
Aug 17 15:15:31 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ibus-pinyin.rtupdate rtupdate python2.7 python2.7
Aug 17 15:15:32 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/alacarte.rtupdate rtupdate python2.7 python2.7
Aug 17 15:15:32 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/catfish.rtupdate rtupdate python2.7 python2.7
Aug 17 15:15:33 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/onboard.rtupdate rtupdate python2.7 python2.7
Aug 17 15:15:33 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ibus.rtupdate rtupdate python2.7 python2.7
Aug 17 15:15:34 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ubiquity-frontend-gtk.rtupdate rtupdate python2.7 python2.7
Aug 17 15:15:34 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/launchpad-integration.rtupdate rtupdate python2.7 python2.7
Aug 17 15:15:34 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/gimp.rtupdate rtupdate python2.7 python2.7
Aug 17 15:15:35 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ibus-table.rtupdate rtupdate python2.7 python2.7
Aug 17 15:15:36 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/software-center.rtupdate rtupdate python2.7 python2.7
Aug 17 15:15:37 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/apport.rtupdate rtupdate python2.7 python2.7
Aug 17 15:15:38 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/apt-xapian-index.rtupdate rtupdate python2.7 python2.7
Aug 17 15:15:39 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/hplip-data.rtupdate rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ubiquity.rtupdate rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ibus-pinyin.rtupdate post-rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/alacarte.rtupdate post-rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/catfish.rtupdate post-rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/onboard.rtupdate post-rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ibus.rtupdate post-rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ubiquity-frontend-gtk.rtupdate post-rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/launchpad-integration.rtupdate post-rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/gimp.rtupdate post-rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ibus-table.rtupdate post-rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/software-center.rtupdate post-rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/apport.rtupdate post-rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/apt-xapian-index.rtupdate post-rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/hplip-data.rtupdate post-rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ubiquity.rtupdate post-rtupdate python2.7 python2.7
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Aug 17 15:15:41 xubuntu plugininstall.py: log-output -t ubiquity umount /target/dev
Aug 17 15:15:42 xubuntu ubiquity: umount: /target/cdrom: not found
Aug 17 15:15:42 xubuntu ubiquity: 
Aug 17 15:15:42 xubuntu plugininstall.py: log-output -t ubiquity umount /target/cdrom
Aug 17 15:15:42 xubuntu ubiquity: mount: warning: /target/cdrom seems to be mounted read-only.
Aug 17 15:15:42 xubuntu plugininstall.py: log-output -t ubiquity mount --bind /cdrom /target/cdrom
Aug 17 15:15:42 xubuntu ubiquity: /usr/lib/ubiquity/apt-setup/generators/01setup: 9: /usr/lib/ubiquity/apt-setup/generators/01setup: 
Aug 17 15:15:42 xubuntu ubiquity: cannot open /target/etc/apt/sources.list: No such file
Aug 17 15:15:42 xubuntu ubiquity: 
Aug 17 15:15:47 xubuntu in-target: Reading package lists...
Aug 17 15:15:49 xubuntu in-target: 
Aug 17 15:15:49 xubuntu apt-setup: Using CD-ROM mount point /cdrom/
Aug 17 15:15:49 xubuntu apt-setup: Identifying.. 
Aug 17 15:15:49 xubuntu apt-setup: [b7690b98a1004dfcedbf38463eab1ccf-2]
Aug 17 15:15:49 xubuntu apt-setup: Scanning disc for index files..
Aug 17 15:15:50 xubuntu apt-setup: Found 4 package indices, 0 source indices, 0 translation indices and 1 signatures
Aug 17 15:15:50 xubuntu apt-setup: Found label: Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)
Aug 17 15:15:50 xubuntu apt-setup: This disc is called: 
Aug 17 15:15:50 xubuntu apt-setup: 'Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)'
Aug 17 15:15:50 xubuntu apt-setup: Copying package lists...
Aug 17 15:15:50 xubuntu apt-setup: gpgv: 
Aug 17 15:15:50 xubuntu apt-setup: Signature made Mon 23 Apr 2012 14:34:44 BST using DSA key ID FBB75451
Aug 17 15:15:50 xubuntu apt-setup: gpgv: 
Aug 17 15:15:50 xubuntu apt-setup: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Aug 17 15:15:50 xubuntu apt-setup: 
Aug 17 15:15:50 xubuntu apt-setup: #015Reading Package Indexes... 0%#015
Aug 17 15:15:50 xubuntu apt-setup: #015Reading Package Indexes... 11%#015
Aug 17 15:15:50 xubuntu apt-setup: #015Reading Package Indexes... Done#015
Aug 17 15:15:50 xubuntu apt-setup: 
Aug 17 15:15:50 xubuntu apt-setup: Writing new source list
Aug 17 15:15:50 xubuntu apt-setup: Source list entries for this disc are:
Aug 17 15:15:50 xubuntu apt-setup: deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main multiverse restricted universe
Aug 17 15:15:50 xubuntu apt-setup: Repeat this process for the rest of the CDs in your set.
Aug 17 15:15:50 xubuntu apt-setup: W
Aug 17 15:15:50 xubuntu apt-setup: : 
Aug 17 15:15:50 xubuntu apt-setup: Skipping nonexistent file /cdrom/dists/precise/main/binary-i386/Packages
Aug 17 15:15:50 xubuntu apt-setup: 
Aug 17 15:15:50 xubuntu apt-setup: W
Aug 17 15:15:50 xubuntu apt-setup: : 
Aug 17 15:15:50 xubuntu apt-setup: Skipping nonexistent file /cdrom/dists/precise/multiverse/binary-i386/Packages
Aug 17 15:15:50 xubuntu apt-setup: 
Aug 17 15:15:50 xubuntu apt-setup: W
Aug 17 15:15:50 xubuntu apt-setup: : 
Aug 17 15:15:50 xubuntu apt-setup: Skipping nonexistent file /cdrom/dists/precise/restricted/binary-i386/Packages
Aug 17 15:15:50 xubuntu apt-setup: 
Aug 17 15:15:50 xubuntu apt-setup: W
Aug 17 15:15:50 xubuntu apt-setup: : 
Aug 17 15:15:50 xubuntu apt-setup: Skipping nonexistent file /cdrom/dists/precise/universe/binary-i386/Packages
Aug 17 15:15:50 xubuntu apt-setup: 
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise InRelease
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main TranslationIndex
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/multiverse TranslationIndex
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted TranslationIndex
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/universe TranslationIndex
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main Translation-en_GB
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main Translation-en
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main Translation-en_GB.UTF-8
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/multiverse Translation-en_GB
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/multiverse Translation-en
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/multiverse Translation-en_GB.UTF-8
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted Translation-en_GB
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted Translation-en
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted Translation-en_GB.UTF-8
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/universe Translation-en_GB
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/universe Translation-en
Aug 17 15:15:52 xubuntu in-target: Ign cdrom://Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/universe Translation-en_GB.UTF-8
Aug 17 15:15:52 xubuntu in-target: Reading package lists...
Aug 17 15:15:52 xubuntu in-target: 
Aug 17 15:15:54 xubuntu choose-mirror[9480]: INFO: base system installable from CD; skipping mirror check
Aug 17 15:15:54 xubuntu choose-mirror[9480]: INFO: base system installable from CD; skipping architecture check
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:13 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:14 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:15 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise InRelease
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates InRelease
Aug 17 15:16:16 xubuntu in-target: Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports InRelease
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg [198 B]
Aug 17 15:16:16 xubuntu in-target: Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:16 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:16 xubuntu rsyslogd-2177: imuxsock begins to drop messages from pid 9779 due to rate-limiting
Aug 17 15:16:19 xubuntu rsyslogd-2177: imuxsock lost 386 messages from pid 9779 due to rate-limiting
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:19 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:20 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:21 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:22 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources [155 kB]
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:23 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:23 xubuntu rsyslogd-2177: imuxsock begins to drop messages from pid 9779 due to rate-limiting
Aug 17 15:16:25 xubuntu rsyslogd-2177: imuxsock lost 182 messages from pid 9779 due to rate-limiting
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:25 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:26 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:27 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:28 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:29 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:29 xubuntu rsyslogd-2177: imuxsock begins to drop messages from pid 9779 due to rate-limiting
Aug 17 15:16:31 xubuntu rsyslogd-2177: imuxsock lost 94 messages from pid 9779 due to rate-limiting
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex [3,706 B]
Aug 17 15:16:31 xubuntu in-target: Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex [2,676 B]
Aug 17 15:16:31 xubuntu in-target: Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex [2,596 B]
Aug 17 15:16:31 xubuntu in-target: Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex [2,922 B]
Aug 17 15:16:31 xubuntu in-target: Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources [156 kB]
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:31 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources [3,285 B]
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources [47.2 kB]
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources [3,108 B]
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages [375 kB]
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:32 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:32 xubuntu rsyslogd-2177: imuxsock begins to drop messages from pid 9779 due to rate-limiting
Aug 17 15:16:37 xubuntu rsyslogd-2177: imuxsock lost 1293 messages from pid 9779 due to rate-limiting
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:37 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Get:51 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB [96.4 kB]
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:38 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:38 xubuntu rsyslogd-2177: imuxsock begins to drop messages from pid 9779 due to rate-limiting
Aug 17 15:16:43 xubuntu rsyslogd-2177: imuxsock lost 1240 messages from pid 9779 due to rate-limiting
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 276, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:43 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:43 xubuntu rsyslogd-2177: imuxsock begins to drop messages from pid 9779 due to rate-limiting
Aug 17 15:16:49 xubuntu rsyslogd-2177: imuxsock lost 334 messages from pid 9779 due to rate-limiting
Aug 17 15:16:49 xubuntu in-target: 
Aug 17 15:16:49 xubuntu in-target: Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66, <GEN0> line 143.
Aug 17 15:16:49 xubuntu in-target: Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67, <GEN0> line 143.
Aug 17 15:16:49 xubuntu in-target: Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68, <GEN0> line 143.
Aug 17 15:16:49 xubuntu in-target: Use of uninitialized value in string ne at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 263, <GEN0> line 143.
Aug 17 15:16:50 xubuntu plugininstall.py: log-output -t ubiquity umount /target/cdrom
Aug 17 15:16:50 xubuntu ubiquity: grep: /target/etc/apt/sources.list: No such file or directory
Aug 17 15:16:50 xubuntu plugininstall.py: Exception during installation:
Aug 17 15:16:50 xubuntu plugininstall.py: Traceback (most recent call last):
Aug 17 15:16:50 xubuntu plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 1735, in <module>
Aug 17 15:16:50 xubuntu plugininstall.py:     install.run()
Aug 17 15:16:50 xubuntu plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 55, in wrapper
Aug 17 15:16:50 xubuntu plugininstall.py:     func(self)
Aug 17 15:16:50 xubuntu plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 163, in run
Aug 17 15:16:50 xubuntu plugininstall.py:     self.configure_apt()
Aug 17 15:16:50 xubuntu plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 637, in configure_apt
Aug 17 15:16:50 xubuntu plugininstall.py:     raise install_misc.InstallStepError("AptSetup failed with code %d" % ret)
Aug 17 15:16:50 xubuntu plugininstall.py: InstallStepError: AptSetup failed with code 141
Aug 17 15:16:50 xubuntu plugininstall.py: 
Aug 17 15:17:01 xubuntu CRON[9996]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 17 15:17:40 xubuntu kernel: [  450.008019] [Hardware Error]: Machine check events logged
Aug 17 15:18:09 xubuntu kernel: [  478.940776] [drm] nouveau 0000:02:00.0: Setting dpms mode 3 on vga encoder (output 1)
Aug 17 15:18:09 xubuntu kernel: [  479.611017] [drm] nouveau 0000:02:00.0: Setting dpms mode 0 on vga encoder (output 1)
Aug 17 15:18:09 xubuntu kernel: [  479.611022] [drm] nouveau 0000:02:00.0: Output VGA-2 is running on CRTC 1 using output B
Aug 17 15:18:10 xubuntu acpid: client 3152[0:0] has disconnected
Aug 17 15:18:10 xubuntu acpid: client connected from 10013[0:0]
Aug 17 15:18:10 xubuntu acpid: 1 client rule loaded
Aug 17 15:18:10 xubuntu kernel: [  479.916022] [drm] nouveau 0000:02:00.0: Load detected on output B
Aug 17 15:18:10 xubuntu kernel: [  480.000020] [drm] nouveau 0000:02:00.0: Load detected on output B
Aug 17 15:18:10 xubuntu kernel: [  480.049238] [drm] nouveau 0000:02:00.0: Setting dpms mode 3 on vga encoder (output 1)
Aug 17 15:18:10 xubuntu kernel: [  480.719671] [drm] nouveau 0000:02:00.0: Setting dpms mode 0 on vga encoder (output 1)
Aug 17 15:18:10 xubuntu kernel: [  480.719677] [drm] nouveau 0000:02:00.0: Output VGA-2 is running on CRTC 1 using output B
Aug 17 15:18:11 xubuntu kernel: [  481.584100] [drm] nouveau 0000:02:00.0: Load detected on output B
Aug 17 15:18:11 xubuntu kernel: [  481.684083] [drm] nouveau 0000:02:00.0: Load detected on output B
Aug 17 15:18:12 xubuntu kernel: [  482.412074] [drm] nouveau 0000:02:00.0: Load detected on output B
Aug 17 15:18:13 xubuntu dbus[1284]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Aug 17 15:18:13 xubuntu dbus[1284]: [system] Successfully activated service 'org.freedesktop.UPower'
Aug 17 15:18:13 xubuntu kernel: [  483.604089] [drm] nouveau 0000:02:00.0: Load detected on output B
Aug 17 15:18:14 xubuntu dbus[1284]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Aug 17 15:18:14 xubuntu dbus[1284]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Aug 17 15:18:14 xubuntu rtkit-daemon[10294]: Successfully called chroot.
Aug 17 15:18:14 xubuntu rtkit-daemon[10294]: Successfully dropped privileges.
Aug 17 15:18:14 xubuntu rtkit-daemon[10294]: Successfully limited resources.
Aug 17 15:18:14 xubuntu rtkit-daemon[10294]: Running.
Aug 17 15:18:14 xubuntu rtkit-daemon[10294]: Successfully made thread 10291 of process 10291 (n/a) owned by '999' high priority at nice level -11.
Aug 17 15:18:14 xubuntu rtkit-daemon[10294]: Supervising 1 threads of 1 processes of 1 users.
Aug 17 15:18:14 xubuntu rtkit-daemon[10294]: Watchdog thread running.
Aug 17 15:18:14 xubuntu rtkit-daemon[10294]: Canary thread running.
Aug 17 15:18:15 xubuntu rtkit-daemon[10294]: Successfully made thread 10303 of process 10291 (n/a) owned by '999' RT at priority 5.
Aug 17 15:18:15 xubuntu rtkit-daemon[10294]: Supervising 2 threads of 1 processes of 1 users.
Aug 17 15:18:15 xubuntu rtkit-daemon[10294]: Successfully made thread 10304 of process 10291 (n/a) owned by '999' RT at priority 5.
Aug 17 15:18:15 xubuntu rtkit-daemon[10294]: Supervising 3 threads of 1 processes of 1 users.
Aug 17 15:18:21 xubuntu dbus[1284]: [system] Activating service name='com.ubuntu.DeviceDriver' (using servicehelper)
Aug 17 15:18:22 xubuntu dbus[1284]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Aug 17 15:18:23 xubuntu dbus[1284]: [system] Successfully activated service 'com.ubuntu.DeviceDriver'
Aug 17 15:18:23 xubuntu blueman-mechanism: Starting blueman-mechanism 
Aug 17 15:18:23 xubuntu dbus[1284]: [system] Successfully activated service 'org.blueman.Mechanism'
Aug 17 15:18:23 xubuntu blueman-mechanism: loading Config 
Aug 17 15:18:23 xubuntu blueman-mechanism: loading Network 
Aug 17 15:18:23 xubuntu blueman-mechanism: loading Ppp 
Aug 17 15:18:23 xubuntu blueman-mechanism: loading RfKill 
Aug 17 15:18:53 xubuntu blueman-mechanism: Exiting 
Aug 17 15:18:55 xubuntu kernel: [  525.008025] [Hardware Error]: Machine check events logged
Aug 17 15:24:14 xubuntu kernel: [  843.728023] mce_notify_irq: 1 callbacks suppressed
Aug 17 15:24:14 xubuntu kernel: [  843.728028] [Hardware Error]: Machine check events logged
Aug 17 15:25:28 xubuntu kernel: [  918.720034] [Hardware Error]: Machine check events logged
Aug 17 15:26:34 xubuntu kernel: [  984.336025] mce_notify_irq: 2 callbacks suppressed
Aug 17 15:26:34 xubuntu kernel: [  984.336030] [Hardware Error]: Machine check events logged
Aug 17 15:26:39 xubuntu kernel: [  989.020021] [Hardware Error]: Machine check events logged
Aug 17 15:28:03 xubuntu kernel: [ 1073.260026] mce_notify_irq: 3 callbacks suppressed
Aug 17 15:28:03 xubuntu kernel: [ 1073.260030] [Hardware Error]: Machine check events logged
Aug 17 15:28:12 xubuntu kernel: [ 1082.620031] [Hardware Error]: Machine check events logged
Aug 17 15:29:22 xubuntu kernel: [ 1152.712022] mce_notify_irq: 8 callbacks suppressed
Aug 17 15:29:22 xubuntu kernel: [ 1152.712026] [Hardware Error]: Machine check events logged
Aug 17 15:29:27 xubuntu kernel: [ 1157.384021] [Hardware Error]: Machine check events logged
Aug 17 15:30:58 xubuntu kernel: [ 1248.488023] mce_notify_irq: 3 callbacks suppressed
Aug 17 15:30:58 xubuntu kernel: [ 1248.488027] [Hardware Error]: Machine check events logged
Aug 17 15:31:08 xubuntu kernel: [ 1257.832034] [Hardware Error]: Machine check events logged

Here is the the data from the dm file:


X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux xubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686
Kernel command line: cdrom-detect/try-usb=true file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash -- BOOT_IMAGE=/casper/vmlinuz 
Build Date: 04 April 2012  11:58:38PM
xorg-server 2:1.11.4-0ubuntu10 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.24.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 17 15:10:44 2012
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) Failed to load module "nv" (module does not exist, 0)
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) Failed to load module "nv" (module does not exist, 0)
resize called 1024 768

(xfwm4:3243): GLib-CRITICAL **: g_str_has_prefix: assertion `prefix != NULL' failed

(ibus-daemon:3247): GLib-GIO-WARNING **: unknown control message type 1:2
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon

(xfwm4:3243): GLib-WARNING **: (/build/buildd/glib2.0-2.32.1/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)

(xfwm4:3243): xfwm4-WARNING **: Failed to connect to session manager: Failed to connect to the session manager: SESSION_MANAGER environment variable not defined
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
** Message: PID 1914 (we are 3246) sent signal 15, shutting down...
** Message: moving back from GtkStatusIcon to indicator

(nm-applet:3246): Gtk-CRITICAL **: gtk_status_icon_set_visible: assertion `GTK_IS_STATUS_ICON (status_icon)' failed
xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
 ddxSigGiveUp: Closing log
Server terminated successfully (0). Closing log file.

and here is the data from the debug file:

Ubiquity 2.10.16

(ubiquity:3259): Pango-WARNING **: error opening config file '/root/.pangorc': Permission denied


(gst-plugin-scanner:3316): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied

(gst-plugin-scanner:3316): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(gst-plugin-scanner:3316): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(gst-plugin-scanner:3316): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(gst-plugin-scanner:3316): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running

Error opening file for reading: Permission denied
No such schema 'org.gnome.settings-daemon.plugins.power'
No such schema 'com.canonical.indicator.session'
update_release_notes_label()
update_release_notes_label()
No such schema 'com.canonical.indicator.session'
No such schema 'com.canonical.indicator.session'
No such schema 'com.canonical.indicator.session'
Error opening file for reading: Permission denied

** (ubiquity:3259): CRITICAL **: unable to create '/root/.cache/dconf'; dconf will not work properly.


I really don't get why it it's not working. I have an old laptop and it worked fine on it right away.

Any help is mush appreciated.

---

### Post by gaiusross on 2012-08-22
I have managed to get ubuntu working. I installed 10.4 and it installed fine with no problems. I then used the upgrade button in the updates window to upgrade all the way to 11.10. I didn't want to go any further incase it messed things up. It now has the same desktop as 12.4. Only thing is, is that it has trouble playing youtube and some online videos don't play at all. Has anyone got any ideas?

Thanks.

---

### Post by mastablasta on 2012-08-22
12.04 has pae kernel. but Lubuntu still has nonPAE kernel (like old editions). perhaps try to install that one and then add Ubuntu desktop to it.
 
additionaly you could try with boot options as mentioned.

---

