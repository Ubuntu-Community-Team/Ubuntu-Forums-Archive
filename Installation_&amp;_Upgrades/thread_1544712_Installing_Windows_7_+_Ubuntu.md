---
title: "Installing Windows 7 + Ubuntu"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by MindGizmoWizard on 2010-08-02
Hello world!

I'm trying to install Ubuntu 10.4 along with Windows 7 right now...
I have a 1 Tb HD and I partitioned it with Windows 7 so that there's 250 Gb of unallocated space.
I installed Windows 7 first as suggester here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

My problem is that the Ubuntu installation is completely empty at step 4. It doesn't show anything.

Halp plx? :)

---

### Post by JustinR on 2010-08-02
> **MindGizmoWizard said:**
> Hello world!

I'm trying to install Ubuntu 10.4 along with Windows 7 right now...
I have a 1 Tb HD and I partitioned it with Windows 7 so that there's 250 Gb of unallocated space.
I installed Windows 7 first as suggester here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

My problem is that the Ubuntu installation is completely empty at step 4. It doesn't show anything.

Halp plx? :)

What do you mean completely empty?

---

### Post by MindGizmoWizard on 2010-08-03
Here's a screenshot.

---

### Post by JustinR on 2010-08-03
> **MindGizmoWizard said:**
> Here's a screenshot.

It doesn't recognize your hard drive, it seems.

Can you boot up the Live-CD and attach the log file /var/log/messages?

---

### Post by MindGizmoWizard on 2010-08-03
...Total noob here, by the way.

I have the Ubuntu 10.04 LTS CD burned from the .iso I downloaded...
...what else do I need to do to attach that log file?

---

### Post by JustinR on 2010-08-03
> **MindGizmoWizard said:**
> ...Total noob here, by the way.

I have the Ubuntu 10.04 LTS CD burned from the .iso I downloaded...
...what else do I need to do to attach that log file?

Hi,

You can use the Live-CD to log on into the Ubuntu Forums, then make a new post, write below the post their is a button called 'Manage Attachments', click that and add a new attachment - navigate to /var/log/messages and press 'Okay'. Then thats it!

---

### Post by MindGizmoWizard on 2010-08-03
Here it is!

Thanks a lot!

---

### Post by MindGizmoWizard on 2010-08-03
...it says "Invalid File" when I try to upload it...

---

### Post by kwilson090507 on 2010-08-03
Just out of curiosity...did you ever see a screen that gave you the option to install Windows 7 and Ubuntu side by side (should have been the previous screen).

BTW-  I'm new to Linux, but over the past month, have completely formatted my drive, installed Ubuntu Desktop, then set up a VirtualBox with a Windows 7 installation in case I needed it.  I'm an IT Manager (10+) years, working in a Microsoft environment.  I haven't even used my virtual installation since I installed it.

---

### Post by JustinR on 2010-08-03
> **MindGizmoWizard said:**
> ...it says "Invalid File" when I try to upload it...

Okay well can you use Applications > Accessories > gedit to open '/var/log/messages' and paste it into a new post with [quote] tags - that should work!

---

### Post by Elmer Fudd on 2010-08-03
Can you run GParted from the live CD, select the 1Tb drive and post a screen shot?

---

### Post by MindGizmoWizard on 2010-08-03
GParted does the same as the Ubuntu Install: everything's just empty.

I opened the messages with gedit and saved it on desktop. Here's the text:
Aug  3 14:23:10 ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Aug  3 14:23:10 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1210" x-info="http://www.rsyslog.com"] (re)start
Aug  3 14:23:10 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Aug  3 14:23:10 ubuntu rsyslogd: rsyslogd's userid changed to 101
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Linux version 2.6.32-21-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
Aug  3 14:23:10 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Aug  3 14:23:10 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfbb0000 (usable)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000dfbb0000 - 00000000dfbe2000 (ACPI NVS)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000dfbe2000 - 00000000dfbf0000 (ACPI data)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000dfbf0000 - 00000000dfc00000 (reserved)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] DMI 2.4 present.
Aug  3 14:23:10 ubuntu kernel: [    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug  3 14:23:10 ubuntu kernel: [    0.000000] last_pfn = 0xdfbb0 max_arch_pfn = 0x400000000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Scanning 1 areas for low memory corruption
Aug  3 14:23:10 ubuntu kernel: [    0.000000] modified physical RAM map:
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 00000000dfbb0000 (usable)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  modified: 00000000dfbb0000 - 00000000dfbe2000 (ACPI NVS)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  modified: 00000000dfbe2000 - 00000000dfbf0000 (ACPI data)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  modified: 00000000dfbf0000 - 00000000dfc00000 (reserved)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  modified: 00000000f4000000 - 00000000f8000000 (reserved)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Aug  3 14:23:10 ubuntu kernel: [    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000dfbb0000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Aug  3 14:23:10 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Aug  3 14:23:10 ubuntu kernel: [    0.000000] RAMDISK: 7f69e000 - 7ffffcaf
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: RSDP 00000000000f7680 00014 (v00 GBT   )
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: RSDT 00000000dfbe2040 00040 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: FACP 00000000dfbe20c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: DSDT 00000000dfbe2180 057D6 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: FACS 00000000dfbb0000 00040
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: HPET 00000000dfbe7ac0 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: MCFG 00000000dfbe7b40 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: EUDS 00000000dfbe7c00 00560 (v01 GBT             00000000      00000000)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: TAMG 00000000dfbe8160 00A32 (v01 GBT    GBT   B0 5455312E BG?? 53450101)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: APIC 00000000dfbe79c0 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: SSDT 00000000dfbe8ba0 02D2C (v01  INTEL PPM RCM  80000001 INTL 20061109)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] No NUMA configuration found
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Faking a node at 0000000000000000-0000000120000000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   NODE_DATA [000000000000d000 - 0000000000011fff]
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   bootmap [0000000000012000 -  0000000000035fff] pages 24
Aug  3 14:23:10 ubuntu kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0120000000]
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   #3 [007f69e000 - 007ffffcaf]          RAMDISK ==> [007f69e000 - 007ffffcaf]
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   #5 [0001a2a000 - 0001a2a0f6]              BRK ==> [0001a2a000 - 0001a2a0f6]
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   #6 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   #7 [000000c000 - 000000d000]          PGTABLE ==> [000000c000 - 000000d000]
Aug  3 14:23:10 ubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000f5890] f5890
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Zone PFN ranges:
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Aug  3 14:23:10 ubuntu kernel: [    0.000000]   Normal   0x00100000 -> 0x00120000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Aug  3 14:23:10 ubuntu kernel: [    0.000000] early_node_map[4] active PFN ranges
Aug  3 14:23:10 ubuntu kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Aug  3 14:23:10 ubuntu kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Aug  3 14:23:10 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x000dfbb0
Aug  3 14:23:10 ubuntu kernel: [    0.000000]     0: 0x00100000 -> 0x00120000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] enabled)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x01] enabled)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x03] enabled)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug  3 14:23:10 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug  3 14:23:10 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
Aug  3 14:23:10 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000dfbb0000 - 00000000dfbe2000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000dfbe2000 - 00000000dfbf0000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000dfbf0000 - 00000000dfc00000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000dfc00000 - 00000000f4000000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000f8000000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fec00000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Allocating PCI resources starting at dfc00000 (gap: dfc00000:14400000)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug  3 14:23:10 ubuntu kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
Aug  3 14:23:10 ubuntu kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u262144
Aug  3 14:23:10 ubuntu kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u262144 alloc=1*2097152
Aug  3 14:23:10 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031138
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Policy zone: Normal
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
Aug  3 14:23:10 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Initializing CPU#0
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Checking aperture...
Aug  3 14:23:10 ubuntu kernel: [    0.000000] No AGP bridge found
Aug  3 14:23:10 ubuntu kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Memory: 4042908k/4718592k available (5409k kernel code, 529112k absent, 146572k reserved, 2976k data, 876k init)
Aug  3 14:23:10 ubuntu kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Aug  3 14:23:10 ubuntu kernel: [    0.000000] NR_IRQS:4352 nr_irqs:472
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Aug  3 14:23:10 ubuntu kernel: [    0.000000] console [tty0] enabled
Aug  3 14:23:10 ubuntu kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Aug  3 14:23:10 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug  3 14:23:10 ubuntu kernel: [    0.000000] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
Aug  3 14:23:10 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Aug  3 14:23:10 ubuntu kernel: [    0.010000] Detected 2931.040 MHz processor.
Aug  3 14:23:10 ubuntu kernel: [    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5862.08 BogoMIPS (lpj=29310400)
Aug  3 14:23:10 ubuntu kernel: [    0.000016] Security Framework initialized
Aug  3 14:23:10 ubuntu kernel: [    0.000029] AppArmor: AppArmor initialized
Aug  3 14:23:10 ubuntu kernel: [    0.000254] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Aug  3 14:23:10 ubuntu kernel: [    0.001366] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Aug  3 14:23:10 ubuntu kernel: [    0.001863] Mount-cache hash table entries: 256
Aug  3 14:23:10 ubuntu kernel: [    0.001944] Initializing cgroup subsys ns
Aug  3 14:23:10 ubuntu kernel: [    0.001946] Initializing cgroup subsys cpuacct
Aug  3 14:23:10 ubuntu kernel: [    0.001949] Initializing cgroup subsys memory
Aug  3 14:23:10 ubuntu kernel: [    0.001953] Initializing cgroup subsys devices
Aug  3 14:23:10 ubuntu kernel: [    0.001954] Initializing cgroup subsys freezer
Aug  3 14:23:10 ubuntu kernel: [    0.001955] Initializing cgroup subsys net_cls
Aug  3 14:23:10 ubuntu kernel: [    0.001967] CPU: Physical Processor ID: 0
Aug  3 14:23:10 ubuntu kernel: [    0.001968] CPU: Processor Core ID: 0
Aug  3 14:23:10 ubuntu kernel: [    0.001971] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  3 14:23:10 ubuntu kernel: [    0.001972] CPU: L2 cache: 256K
Aug  3 14:23:10 ubuntu kernel: [    0.001973] CPU: L3 cache: 8192K
Aug  3 14:23:10 ubuntu kernel: [    0.001975] CPU 0/0x0 -> Node 0
Aug  3 14:23:10 ubuntu kernel: [    0.001977] mce: CPU supports 9 MCE banks
Aug  3 14:23:10 ubuntu kernel: [    0.001984] CPU0: Thermal monitoring enabled (TM1)
Aug  3 14:23:10 ubuntu kernel: [    0.001987] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6 CMCI:8
Aug  3 14:23:10 ubuntu kernel: [    0.001992] using mwait in idle threads.
Aug  3 14:23:10 ubuntu kernel: [    0.001994] Performance Events: Nehalem/Corei7 events, Intel PMU driver.
Aug  3 14:23:10 ubuntu kernel: [    0.001997] ... version:                3
Aug  3 14:23:10 ubuntu kernel: [    0.001998] ... bit width:              48
Aug  3 14:23:10 ubuntu kernel: [    0.001999] ... generic registers:      4
Aug  3 14:23:10 ubuntu kernel: [    0.002000] ... value mask:             0000ffffffffffff
Aug  3 14:23:10 ubuntu kernel: [    0.002001] ... max period:             000000007fffffff
Aug  3 14:23:10 ubuntu kernel: [    0.002002] ... fixed-purpose events:   3
Aug  3 14:23:10 ubuntu kernel: [    0.002003] ... event mask:             000000070000000f
Aug  3 14:23:10 ubuntu kernel: [    0.003527] ACPI: Core revision 20090903
Aug  3 14:23:10 ubuntu kernel: [    0.013393] ftrace: converting mcount calls to 0f 1f 44 00 00
Aug  3 14:23:10 ubuntu kernel: [    0.013396] ftrace: allocating 22518 entries in 89 pages
Aug  3 14:23:10 ubuntu kernel: [    0.018670] Setting APIC routing to flat
Aug  3 14:23:10 ubuntu kernel: [    0.018996] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug  3 14:23:10 ubuntu kernel: [    0.118899] CPU0: Intel(R) Core(TM) i7 CPU       K 875  @ 2.93GHz stepping 05
Aug  3 14:23:10 ubuntu kernel: [    0.238430] Booting processor 1 APIC 0x2 ip 0x6000
Aug  3 14:23:10 ubuntu kernel: [    0.249151] Initializing CPU#1
Aug  3 14:23:10 ubuntu kernel: [    0.398184] CPU: Physical Processor ID: 0
Aug  3 14:23:10 ubuntu kernel: [    0.398185] CPU: Processor Core ID: 1
Aug  3 14:23:10 ubuntu kernel: [    0.398187] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  3 14:23:10 ubuntu kernel: [    0.398188] CPU: L2 cache: 256K
Aug  3 14:23:10 ubuntu kernel: [    0.398188] CPU: L3 cache: 8192K
Aug  3 14:23:10 ubuntu kernel: [    0.398190] CPU 1/0x2 -> Node 0
Aug  3 14:23:10 ubuntu kernel: [    0.398198] CPU1: Thermal monitoring enabled (TM1)
Aug  3 14:23:10 ubuntu kernel: [    0.398201] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Aug  3 14:23:10 ubuntu kernel: [    0.398241] CPU1: Intel(R) Core(TM) i7 CPU       K 875  @ 2.93GHz stepping 05
Aug  3 14:23:10 ubuntu kernel: [    0.398246] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug  3 14:23:10 ubuntu kernel: [    0.418290] Booting processor 2 APIC 0x4 ip 0x6000
Aug  3 14:23:10 ubuntu kernel: [    0.428615] Initializing CPU#2
Aug  3 14:23:10 ubuntu kernel: [    0.578005] CPU: Physical Processor ID: 0
Aug  3 14:23:10 ubuntu kernel: [    0.578006] CPU: Processor Core ID: 2
Aug  3 14:23:10 ubuntu kernel: [    0.578007] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  3 14:23:10 ubuntu kernel: [    0.578008] CPU: L2 cache: 256K
Aug  3 14:23:10 ubuntu kernel: [    0.578009] CPU: L3 cache: 8192K
Aug  3 14:23:10 ubuntu kernel: [    0.578011] CPU 2/0x4 -> Node 0
Aug  3 14:23:10 ubuntu kernel: [    0.578019] CPU2: Thermal monitoring enabled (TM1)
Aug  3 14:23:10 ubuntu kernel: [    0.578021] CPU 2 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Aug  3 14:23:10 ubuntu kernel: [    0.578102] CPU2: Intel(R) Core(TM) i7 CPU       K 875  @ 2.93GHz stepping 05
Aug  3 14:23:10 ubuntu kernel: [    0.578108] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Aug  3 14:23:10 ubuntu kernel: [    0.598152] Booting processor 3 APIC 0x6 ip 0x6000
Aug  3 14:23:10 ubuntu kernel: [    0.608476] Initializing CPU#3
Aug  3 14:23:10 ubuntu kernel: [    0.757826] CPU: Physical Processor ID: 0
Aug  3 14:23:10 ubuntu kernel: [    0.757827] CPU: Processor Core ID: 3
Aug  3 14:23:10 ubuntu kernel: [    0.757829] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  3 14:23:10 ubuntu kernel: [    0.757830] CPU: L2 cache: 256K
Aug  3 14:23:10 ubuntu kernel: [    0.757830] CPU: L3 cache: 8192K
Aug  3 14:23:10 ubuntu kernel: [    0.757832] CPU 3/0x6 -> Node 0
Aug  3 14:23:10 ubuntu kernel: [    0.757840] CPU3: Thermal monitoring enabled (TM1)
Aug  3 14:23:10 ubuntu kernel: [    0.757843] CPU 3 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Aug  3 14:23:10 ubuntu kernel: [    0.757907] CPU3: Intel(R) Core(TM) i7 CPU       K 875  @ 2.93GHz stepping 05
Aug  3 14:23:10 ubuntu kernel: [    0.757913] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Aug  3 14:23:10 ubuntu kernel: [    0.777958] Booting processor 4 APIC 0x1 ip 0x6000
Aug  3 14:23:10 ubuntu kernel: [    0.788283] Initializing CPU#4
Aug  3 14:23:10 ubuntu kernel: [    0.937647] CPU: Physical Processor ID: 0
Aug  3 14:23:10 ubuntu kernel: [    0.937648] CPU: Processor Core ID: 0
Aug  3 14:23:10 ubuntu kernel: [    0.937650] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  3 14:23:10 ubuntu kernel: [    0.937651] CPU: L2 cache: 256K
Aug  3 14:23:10 ubuntu kernel: [    0.937652] CPU: L3 cache: 8192K
Aug  3 14:23:10 ubuntu kernel: [    0.937654] CPU 4/0x1 -> Node 0
Aug  3 14:23:10 ubuntu kernel: [    0.937663] CPU4: Thermal monitoring enabled (TM1)
Aug  3 14:23:10 ubuntu kernel: [    0.937666] CPU 4 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Aug  3 14:23:10 ubuntu kernel: [    0.937771] CPU4: Intel(R) Core(TM) i7 CPU       K 875  @ 2.93GHz stepping 05
Aug  3 14:23:10 ubuntu kernel: [    0.937778] checking TSC synchronization [CPU#0 -> CPU#4]: passed.
Aug  3 14:23:10 ubuntu kernel: [    0.957826] Booting processor 5 APIC 0x3 ip 0x6000
Aug  3 14:23:10 ubuntu kernel: [    0.968149] Initializing CPU#5
Aug  3 14:23:10 ubuntu kernel: [    1.117467] CPU: Physical Processor ID: 0
Aug  3 14:23:10 ubuntu kernel: [    1.117468] CPU: Processor Core ID: 1
Aug  3 14:23:10 ubuntu kernel: [    1.117470] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  3 14:23:10 ubuntu kernel: [    1.117471] CPU: L2 cache: 256K
Aug  3 14:23:10 ubuntu kernel: [    1.117471] CPU: L3 cache: 8192K
Aug  3 14:23:10 ubuntu kernel: [    1.117473] CPU 5/0x3 -> Node 0
Aug  3 14:23:10 ubuntu kernel: [    1.117481] CPU5: Thermal monitoring enabled (TM1)
Aug  3 14:23:10 ubuntu kernel: [    1.117483] CPU 5 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Aug  3 14:23:10 ubuntu kernel: [    1.117537] CPU5: Intel(R) Core(TM) i7 CPU       K 875  @ 2.93GHz stepping 05
Aug  3 14:23:10 ubuntu kernel: [    1.117543] checking TSC synchronization [CPU#0 -> CPU#5]: passed.
Aug  3 14:23:10 ubuntu kernel: [    1.137587] Booting processor 6 APIC 0x5 ip 0x6000
Aug  3 14:23:10 ubuntu kernel: [    1.147910] Initializing CPU#6
Aug  3 14:23:10 ubuntu kernel: [    1.297288] CPU: Physical Processor ID: 0
Aug  3 14:23:10 ubuntu kernel: [    1.297288] CPU: Processor Core ID: 2
Aug  3 14:23:10 ubuntu kernel: [    1.297290] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  3 14:23:10 ubuntu kernel: [    1.297291] CPU: L2 cache: 256K
Aug  3 14:23:10 ubuntu kernel: [    1.297292] CPU: L3 cache: 8192K
Aug  3 14:23:10 ubuntu kernel: [    1.297294] CPU 6/0x5 -> Node 0
Aug  3 14:23:10 ubuntu kernel: [    1.297302] CPU6: Thermal monitoring enabled (TM1)
Aug  3 14:23:10 ubuntu kernel: [    1.297304] CPU 6 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Aug  3 14:23:10 ubuntu kernel: [    1.297398] CPU6: Intel(R) Core(TM) i7 CPU       K 875  @ 2.93GHz stepping 05
Aug  3 14:23:10 ubuntu kernel: [    1.297404] checking TSC synchronization [CPU#0 -> CPU#6]: passed.
Aug  3 14:23:10 ubuntu kernel: [    1.317451] Booting processor 7 APIC 0x7 ip 0x6000
Aug  3 14:23:10 ubuntu kernel: [    1.327775] Initializing CPU#7
Aug  3 14:23:10 ubuntu kernel: [    1.477108] CPU: Physical Processor ID: 0
Aug  3 14:23:10 ubuntu kernel: [    1.477109] CPU: Processor Core ID: 3
Aug  3 14:23:10 ubuntu kernel: [    1.477111] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  3 14:23:10 ubuntu kernel: [    1.477112] CPU: L2 cache: 256K
Aug  3 14:23:10 ubuntu kernel: [    1.477113] CPU: L3 cache: 8192K
Aug  3 14:23:10 ubuntu kernel: [    1.477114] CPU 7/0x7 -> Node 0
Aug  3 14:23:10 ubuntu kernel: [    1.477122] CPU7: Thermal monitoring enabled (TM1)
Aug  3 14:23:10 ubuntu kernel: [    1.477125] CPU 7 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Aug  3 14:23:10 ubuntu kernel: [    1.477163] CPU7: Intel(R) Core(TM) i7 CPU       K 875  @ 2.93GHz stepping 05
Aug  3 14:23:10 ubuntu kernel: [    1.477169] checking TSC synchronization [CPU#0 -> CPU#7]: passed.
Aug  3 14:23:10 ubuntu kernel: [    1.497163] Brought up 8 CPUs
Aug  3 14:23:10 ubuntu kernel: [    1.497165] Total of 8 processors activated (46898.78 BogoMIPS).
Aug  3 14:23:10 ubuntu kernel: [    1.500728] devtmpfs: initialized
Aug  3 14:23:10 ubuntu kernel: [    1.500942] regulator: core version 0.5
Aug  3 14:23:10 ubuntu kernel: [    1.500965] Time: 14:22:31  Date: 08/03/10
Aug  3 14:23:10 ubuntu kernel: [    1.500992] NET: Registered protocol family 16
Aug  3 14:23:10 ubuntu kernel: [    1.501052] Trying to unpack rootfs image as initramfs...
Aug  3 14:23:10 ubuntu kernel: [    1.501070] ACPI: bus type pci registered
Aug  3 14:23:10 ubuntu kernel: [    1.501114] PCI: MCFG configuration 0: base f4000000 segment 0 buses 0 - 63
Aug  3 14:23:10 ubuntu kernel: [    1.501116] PCI: MCFG area at f4000000 reserved in E820
Aug  3 14:23:10 ubuntu kernel: [    1.502289] PCI: Using MMCONFIG at f4000000 - f7ffffff
Aug  3 14:23:10 ubuntu kernel: [    1.502291] PCI: Using configuration type 1 for base access
Aug  3 14:23:10 ubuntu kernel: [    1.502798] bio: create slab <bio-0> at 0
Aug  3 14:23:10 ubuntu kernel: [    1.507905] ACPI: Interpreter enabled
Aug  3 14:23:10 ubuntu kernel: [    1.507908] ACPI: (supports S0 S3 S4 S5)
Aug  3 14:23:10 ubuntu kernel: [    1.507921] ACPI: Using IOAPIC for interrupt routing
Aug  3 14:23:10 ubuntu kernel: [    1.511901] ACPI Warning: Incorrect checksum in table [TAMG] - 10, should be 0F (20090903/tbutils-314)
Aug  3 14:23:10 ubuntu kernel: [    1.511989] ACPI: No dock devices found.
Aug  3 14:23:10 ubuntu kernel: [    1.512060] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug  3 14:23:10 ubuntu kernel: [    1.512152] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Aug  3 14:23:10 ubuntu kernel: [    1.512155] pci 0000:00:03.0: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.512202] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Aug  3 14:23:10 ubuntu kernel: [    1.512204] pci 0000:00:05.0: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.512664] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Aug  3 14:23:10 ubuntu kernel: [    1.512667] pci 0000:00:1a.7: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.512736] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Aug  3 14:23:10 ubuntu kernel: [    1.512739] pci 0000:00:1b.0: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.512791] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Aug  3 14:23:10 ubuntu kernel: [    1.512793] pci 0000:00:1c.0: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.512848] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Aug  3 14:23:10 ubuntu kernel: [    1.512851] pci 0000:00:1c.3: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.512904] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Aug  3 14:23:10 ubuntu kernel: [    1.512907] pci 0000:00:1c.4: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.512961] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
Aug  3 14:23:10 ubuntu kernel: [    1.512964] pci 0000:00:1c.6: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.513017] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
Aug  3 14:23:10 ubuntu kernel: [    1.513019] pci 0000:00:1c.7: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.513347] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Aug  3 14:23:10 ubuntu kernel: [    1.513350] pci 0000:00:1d.7: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.513870] pci 0000:02:00.0: PME# supported from D3hot
Aug  3 14:23:10 ubuntu kernel: [    1.513872] pci 0000:02:00.0: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.514074] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
Aug  3 14:23:10 ubuntu kernel: [    1.514078] pci 0000:04:00.0: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.514254] pci 0000:05:00.0: PME# supported from D3hot
Aug  3 14:23:10 ubuntu kernel: [    1.514258] pci 0000:05:00.0: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.514539] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug  3 14:23:10 ubuntu kernel: [    1.514543] pci 0000:06:00.0: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.514715] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug  3 14:23:10 ubuntu kernel: [    1.514719] pci 0000:07:00.0: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.514930] pci 0000:08:07.0: PME# supported from D0 D1 D2 D3hot
Aug  3 14:23:10 ubuntu kernel: [    1.514933] pci 0000:08:07.0: PME# disabled
Aug  3 14:23:10 ubuntu kernel: [    1.514966] pci 0000:00:1e.0: transparent bridge
Aug  3 14:23:10 ubuntu kernel: [    1.535612] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Aug  3 14:23:10 ubuntu kernel: [    1.535685] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Aug  3 14:23:10 ubuntu kernel: [    1.535756] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
Aug  3 14:23:10 ubuntu kernel: [    1.535828] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Aug  3 14:23:10 ubuntu kernel: [    1.535899] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Aug  3 14:23:10 ubuntu kernel: [    1.535971] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Aug  3 14:23:10 ubuntu kernel: [    1.536042] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Aug  3 14:23:10 ubuntu kernel: [    1.536112] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Aug  3 14:23:10 ubuntu kernel: [    1.536180] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Aug  3 14:23:10 ubuntu kernel: [    1.536184] vgaarb: loaded
Aug  3 14:23:10 ubuntu kernel: [    1.536246] SCSI subsystem initialized
Aug  3 14:23:10 ubuntu kernel: [    1.536366] usbcore: registered new interface driver usbfs
Aug  3 14:23:10 ubuntu kernel: [    1.536372] usbcore: registered new interface driver hub
Aug  3 14:23:10 ubuntu kernel: [    1.536386] usbcore: registered new device driver usb
Aug  3 14:23:10 ubuntu kernel: [    1.536464] ACPI: WMI: Mapper loaded
Aug  3 14:23:10 ubuntu kernel: [    1.536465] PCI: Using ACPI for IRQ routing
Aug  3 14:23:10 ubuntu kernel: [    1.536607] NetLabel: Initializing
Aug  3 14:23:10 ubuntu kernel: [    1.536608] NetLabel:  domain hash size = 128
Aug  3 14:23:10 ubuntu kernel: [    1.536609] NetLabel:  protocols = UNLABELED CIPSOv4
Aug  3 14:23:10 ubuntu kernel: [    1.536617] NetLabel:  unlabeled traffic allowed by default
Aug  3 14:23:10 ubuntu kernel: [    1.536645] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 25, 26, 27, 28, 0
Aug  3 14:23:10 ubuntu kernel: [    1.536650] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Aug  3 14:23:10 ubuntu kernel: [    2.885814] Switching to clocksource tsc
Aug  3 14:23:10 ubuntu kernel: [    2.887050] AppArmor: AppArmor Filesystem Enabled
Aug  3 14:23:10 ubuntu kernel: [    2.887063] pnp: PnP ACPI init
Aug  3 14:23:10 ubuntu kernel: [    2.887075] ACPI: bus type pnp registered
Aug  3 14:23:10 ubuntu kernel: [    2.889320] pnp: PnP ACPI: found 14 devices
Aug  3 14:23:10 ubuntu kernel: [    2.889321] ACPI: ACPI bus type pnp unregistered
Aug  3 14:23:10 ubuntu kernel: [    2.889329] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889331] system 00:01: ioport range 0x290-0x29f has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889333] system 00:01: ioport range 0x800-0x805 has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889334] system 00:01: ioport range 0x290-0x294 has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889336] system 00:01: ioport range 0x880-0x88f has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889341] system 00:0a: ioport range 0x400-0x4cf has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889343] system 00:0a: ioport range 0x4d2-0x4ff has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889347] system 00:0b: iomem range 0xf4000000-0xf7ffffff has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889350] system 00:0c: iomem range 0xcf400-0xcffff has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889352] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889353] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889355] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889357] system 00:0c: iomem range 0xdfbb0000-0xdfbfffff could not be reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889358] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889360] system 00:0c: iomem range 0x100000-0xdfbaffff could not be reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889362] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889364] system 00:0c: iomem range 0xfed10000-0xfed1dfff has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889366] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889367] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889369] system 00:0c: iomem range 0xffb00000-0xffb7ffff has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889371] system 00:0c: iomem range 0xfff00000-0xffffffff has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.889373] system 00:0c: iomem range 0xe0000-0xeffff has been reserved
Aug  3 14:23:10 ubuntu kernel: [    2.894066] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
Aug  3 14:23:10 ubuntu kernel: [    2.894069] pci 0000:00:03.0:   IO window: 0xc000-0xcfff
Aug  3 14:23:10 ubuntu kernel: [    2.894072] pci 0000:00:03.0:   MEM window: 0xfb800000-0xfb8fffff
Aug  3 14:23:10 ubuntu kernel: [    2.894074] pci 0000:00:03.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
Aug  3 14:23:10 ubuntu kernel: [    2.894078] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02
Aug  3 14:23:10 ubuntu kernel: [    2.894080] pci 0000:00:05.0:   IO window: 0xd000-0xdfff
Aug  3 14:23:10 ubuntu kernel: [    2.894083] pci 0000:00:05.0:   MEM window: 0xfb600000-0xfb6fffff
Aug  3 14:23:10 ubuntu kernel: [    2.894085] pci 0000:00:05.0:   PREFETCH window: 0xf0000000-0xf00fffff
Aug  3 14:23:10 ubuntu kernel: [    2.894089] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
Aug  3 14:23:10 ubuntu kernel: [    2.894091] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Aug  3 14:23:10 ubuntu kernel: [    2.894094] pci 0000:00:1c.0:   MEM window: 0xf0100000-0xf02fffff
Aug  3 14:23:10 ubuntu kernel: [    2.894097] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0300000-0x000000f04fffff
Aug  3 14:23:10 ubuntu kernel: [    2.894102] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
Aug  3 14:23:10 ubuntu kernel: [    2.894104] pci 0000:00:1c.3:   IO window: 0x2000-0x2fff
Aug  3 14:23:10 ubuntu kernel: [    2.894107] pci 0000:00:1c.3:   MEM window: 0xfbe00000-0xfbefffff
Aug  3 14:23:10 ubuntu kernel: [    2.894110] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0500000-0x000000f06fffff
Aug  3 14:23:10 ubuntu kernel: [    2.894115] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:05
Aug  3 14:23:10 ubuntu kernel: [    2.894117] pci 0000:00:1c.4:   IO window: 0xb000-0xbfff
Aug  3 14:23:10 ubuntu kernel: [    2.894120] pci 0000:00:1c.4:   MEM window: 0xfbd00000-0xfbdfffff
Aug  3 14:23:10 ubuntu kernel: [    2.894123] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0700000-0x000000f08fffff
Aug  3 14:23:10 ubuntu kernel: [    2.894128] pci 0000:00:1c.6: PCI bridge, secondary bus 0000:06
Aug  3 14:23:10 ubuntu kernel: [    2.894130] pci 0000:00:1c.6:   IO window: 0xa000-0xafff
Aug  3 14:23:10 ubuntu kernel: [    2.894134] pci 0000:00:1c.6:   MEM window: 0xfbc00000-0xfbcfffff
Aug  3 14:23:10 ubuntu kernel: [    2.894136] pci 0000:00:1c.6:   PREFETCH window: 0x000000fbb00000-0x000000fbbfffff
Aug  3 14:23:10 ubuntu kernel: [    2.894141] pci 0000:00:1c.7: PCI bridge, secondary bus 0000:07
Aug  3 14:23:10 ubuntu kernel: [    2.894143] pci 0000:00:1c.7:   IO window: 0x8000-0x8fff
Aug  3 14:23:10 ubuntu kernel: [    2.894147] pci 0000:00:1c.7:   MEM window: 0xfba00000-0xfbafffff
Aug  3 14:23:10 ubuntu kernel: [    2.894150] pci 0000:00:1c.7:   PREFETCH window: 0x000000fb900000-0x000000fb9fffff
Aug  3 14:23:10 ubuntu kernel: [    2.894154] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
Aug  3 14:23:10 ubuntu kernel: [    2.894156] pci 0000:00:1e.0:   IO window: 0x9000-0x9fff
Aug  3 14:23:10 ubuntu kernel: [    2.894160] pci 0000:00:1e.0:   MEM window: 0xfb700000-0xfb7fffff
Aug  3 14:23:10 ubuntu kernel: [    2.894163] pci 0000:00:1e.0:   PREFETCH window: disabled
Aug  3 14:23:10 ubuntu kernel: [    2.894179] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  3 14:23:10 ubuntu kernel: [    2.894186] pci 0000:00:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  3 14:23:10 ubuntu kernel: [    2.894195] pci 0000:00:1c.0: enabling device (0000 -> 0003)
Aug  3 14:23:10 ubuntu kernel: [    2.894198] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  3 14:23:10 ubuntu kernel: [    2.894207] pci 0000:00:1c.3: enabling device (0006 -> 0007)
Aug  3 14:23:10 ubuntu kernel: [    2.894213] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Aug  3 14:23:10 ubuntu kernel: [    2.894221] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  3 14:23:10 ubuntu kernel: [    2.894233] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug  3 14:23:10 ubuntu kernel: [    2.894242] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Aug  3 14:23:10 ubuntu kernel: [    2.894315] NET: Registered protocol family 2
Aug  3 14:23:10 ubuntu kernel: [    2.894430] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Aug  3 14:23:10 ubuntu kernel: [    2.895071] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Aug  3 14:23:10 ubuntu kernel: [    2.897113] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Aug  3 14:23:10 ubuntu kernel: [    2.897380] TCP: Hash tables configured (established 524288 bind 65536)
Aug  3 14:23:10 ubuntu kernel: [    2.897382] TCP reno registered
Aug  3 14:23:10 ubuntu kernel: [    2.897454] NET: Registered protocol family 1
Aug  3 14:23:10 ubuntu kernel: [    2.938804] Scanning for low memory corruption every 60 seconds
Aug  3 14:23:10 ubuntu kernel: [    2.938890] audit: initializing netlink socket (disabled)
Aug  3 14:23:10 ubuntu kernel: [    2.938898] type=2000 audit(1280845351.750:1): initialized
Aug  3 14:23:10 ubuntu kernel: [    2.945496] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Aug  3 14:23:10 ubuntu kernel: [    2.946421] VFS: Disk quotas dquot_6.5.2
Aug  3 14:23:10 ubuntu kernel: [    2.946455] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Aug  3 14:23:10 ubuntu kernel: [    2.946844] fuse init (API version 7.13)
Aug  3 14:23:10 ubuntu kernel: [    2.946894] msgmni has been set to 7896
Aug  3 14:23:10 ubuntu kernel: [    2.947088] alg: No test for stdrng (krng)
Aug  3 14:23:10 ubuntu kernel: [    2.947122] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug  3 14:23:10 ubuntu kernel: [    2.947124] io scheduler noop registered
Aug  3 14:23:10 ubuntu kernel: [    2.947126] io scheduler anticipatory registered
Aug  3 14:23:10 ubuntu kernel: [    2.947127] io scheduler deadline registered
Aug  3 14:23:10 ubuntu kernel: [    2.947150] io scheduler cfq registered (default)
Aug  3 14:23:10 ubuntu kernel: [    2.947865] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug  3 14:23:10 ubuntu kernel: [    2.947944] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug  3 14:23:10 ubuntu kernel: [    2.947996] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Aug  3 14:23:10 ubuntu kernel: [    2.947999] ACPI: Power Button [PWRB]
Aug  3 14:23:10 ubuntu kernel: [    2.948029] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Aug  3 14:23:10 ubuntu kernel: [    2.948030] ACPI: Power Button [PWRF]
Aug  3 14:23:10 ubuntu kernel: [    2.948561] processor LNXCPU:00: registered as cooling_device0
Aug  3 14:23:10 ubuntu kernel: [    3.115878] processor LNXCPU:01: registered as cooling_device1
Aug  3 14:23:10 ubuntu kernel: [    3.116531] processor LNXCPU:02: registered as cooling_device2
Aug  3 14:23:10 ubuntu kernel: [    3.116900] processor LNXCPU:03: registered as cooling_device3
Aug  3 14:23:10 ubuntu kernel: [    3.117257] processor LNXCPU:04: registered as cooling_device4
Aug  3 14:23:10 ubuntu kernel: [    3.117637] processor LNXCPU:05: registered as cooling_device5
Aug  3 14:23:10 ubuntu kernel: [    3.117979] processor LNXCPU:06: registered as cooling_device6
Aug  3 14:23:10 ubuntu kernel: [    3.118381] processor LNXCPU:07: registered as cooling_device7
Aug  3 14:23:10 ubuntu kernel: [    3.119536] Freeing initrd memory: 9607k freed
Aug  3 14:23:10 ubuntu kernel: [    3.120876] Linux agpgart interface v0.103
Aug  3 14:23:10 ubuntu kernel: [    3.120920] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Aug  3 14:23:10 ubuntu kernel: [    3.121020] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug  3 14:23:10 ubuntu kernel: [    3.121244] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug  3 14:23:10 ubuntu kernel: [    3.121858] brd: module loaded
Aug  3 14:23:10 ubuntu kernel: [    3.122115] loop: module loaded
Aug  3 14:23:10 ubuntu kernel: [    3.122165] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Aug  3 14:23:10 ubuntu kernel: [    3.122242] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug  3 14:23:10 ubuntu kernel: [    3.122246] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Aug  3 14:23:10 ubuntu kernel: [    3.122328] scsi0 : ata_piix
Aug  3 14:23:10 ubuntu kernel: [    3.122372] scsi1 : ata_piix
Aug  3 14:23:10 ubuntu kernel: [    3.122773] ata1: SATA max UDMA/133 cmd 0xf800 ctl 0xf700 bmdma 0xf400 irq 17
Aug  3 14:23:10 ubuntu kernel: [    3.122777] ata2: SATA max UDMA/133 cmd 0xf600 ctl 0xf500 bmdma 0xf408 irq 17
Aug  3 14:23:10 ubuntu kernel: [    3.122793] ata_piix 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug  3 14:23:10 ubuntu kernel: [    3.122796] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Aug  3 14:23:10 ubuntu kernel: [    3.122842] scsi2 : ata_piix
Aug  3 14:23:10 ubuntu kernel: [    3.122871] scsi3 : ata_piix
Aug  3 14:23:10 ubuntu kernel: [    3.123204] ata3: SATA max UDMA/133 cmd 0xf100 ctl 0xf000 bmdma 0xed00 irq 17
Aug  3 14:23:10 ubuntu kernel: [    3.123207] ata4: SATA max UDMA/133 cmd 0xef00 ctl 0xee00 bmdma 0xed08 irq 17
Aug  3 14:23:10 ubuntu kernel: [    3.123247] pata_acpi 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  3 14:23:10 ubuntu kernel: [    3.123269] pata_acpi 0000:02:00.0: PCI INT A disabled
Aug  3 14:23:10 ubuntu kernel: [    3.123282] pata_acpi 0000:05:00.1: enabling device (0000 -> 0001)
Aug  3 14:23:10 ubuntu kernel: [    3.123286] pata_acpi 0000:05:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug  3 14:23:10 ubuntu kernel: [    3.123308] pata_acpi 0000:05:00.1: PCI INT B disabled
Aug  3 14:23:10 ubuntu kernel: [    3.123318] pata_acpi 0000:08:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  3 14:23:10 ubuntu kernel: [    3.123334] pata_acpi 0000:08:03.0: PCI INT A disabled
Aug  3 14:23:10 ubuntu kernel: [    3.123492] Fixed MDIO Bus: probed
Aug  3 14:23:10 ubuntu kernel: [    3.123509] PPP generic driver version 2.4.2
Aug  3 14:23:10 ubuntu kernel: [    3.123529] tun: Universal TUN/TAP device driver, 1.6
Aug  3 14:23:10 ubuntu kernel: [    3.123530] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug  3 14:23:10 ubuntu kernel: [    3.123573] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug  3 14:23:10 ubuntu kernel: [    3.123585] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug  3 14:23:10 ubuntu kernel: [    3.123601] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Aug  3 14:23:10 ubuntu kernel: [    3.123625] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Aug  3 14:23:10 ubuntu kernel: [    3.123646] ehci_hcd 0000:00:1a.7: debug port 2
Aug  3 14:23:10 ubuntu kernel: [    3.127539] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfbfff000
Aug  3 14:23:10 ubuntu kernel: [    3.150067] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Aug  3 14:23:10 ubuntu kernel: [    3.150115] usb usb1: configuration #1 chosen from 1 choice
Aug  3 14:23:10 ubuntu kernel: [    3.150132] hub 1-0:1.0: USB hub found
Aug  3 14:23:10 ubuntu kernel: [    3.150136] hub 1-0:1.0: 6 ports detected
Aug  3 14:23:10 ubuntu kernel: [    3.150180] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug  3 14:23:10 ubuntu kernel: [    3.150190] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug  3 14:23:10 ubuntu kernel: [    3.150207] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Aug  3 14:23:10 ubuntu kernel: [    3.150226] ehci_hcd 0000:00:1d.7: debug port 2
Aug  3 14:23:10 ubuntu kernel: [    3.154126] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfbffe000
Aug  3 14:23:10 ubuntu kernel: [    3.180032] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Aug  3 14:23:10 ubuntu kernel: [    3.180073] usb usb2: configuration #1 chosen from 1 choice
Aug  3 14:23:10 ubuntu kernel: [    3.180087] hub 2-0:1.0: USB hub found
Aug  3 14:23:10 ubuntu kernel: [    3.180090] hub 2-0:1.0: 8 ports detected
Aug  3 14:23:10 ubuntu kernel: [    3.180129] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug  3 14:23:10 ubuntu kernel: [    3.180137] uhci_hcd: USB Universal Host Controller Interface driver
Aug  3 14:23:10 ubuntu kernel: [    3.180151] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  3 14:23:10 ubuntu kernel: [    3.180158] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Aug  3 14:23:10 ubuntu kernel: [    3.180176] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Aug  3 14:23:10 ubuntu kernel: [    3.180202] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
Aug  3 14:23:10 ubuntu kernel: [    3.180255] usb usb3: configuration #1 chosen from 1 choice
Aug  3 14:23:10 ubuntu kernel: [    3.180269] hub 3-0:1.0: USB hub found
Aug  3 14:23:10 ubuntu kernel: [    3.180273] hub 3-0:1.0: 2 ports detected
Aug  3 14:23:10 ubuntu kernel: [    3.180305] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Aug  3 14:23:10 ubuntu kernel: [    3.180312] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Aug  3 14:23:10 ubuntu kernel: [    3.180329] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Aug  3 14:23:10 ubuntu kernel: [    3.180354] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
Aug  3 14:23:10 ubuntu kernel: [    3.180404] usb usb4: configuration #1 chosen from 1 choice
Aug  3 14:23:10 ubuntu kernel: [    3.180418] hub 4-0:1.0: USB hub found
Aug  3 14:23:10 ubuntu kernel: [    3.180421] hub 4-0:1.0: 2 ports detected
Aug  3 14:23:10 ubuntu kernel: [    3.180449] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug  3 14:23:10 ubuntu kernel: [    3.180455] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Aug  3 14:23:10 ubuntu kernel: [    3.180476] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Aug  3 14:23:10 ubuntu kernel: [    3.180495] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000fd00
Aug  3 14:23:10 ubuntu kernel: [    3.180548] usb usb5: configuration #1 chosen from 1 choice
Aug  3 14:23:10 ubuntu kernel: [    3.180561] hub 5-0:1.0: USB hub found
Aug  3 14:23:10 ubuntu kernel: [    3.180564] hub 5-0:1.0: 2 ports detected
Aug  3 14:23:10 ubuntu kernel: [    3.180591] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug  3 14:23:10 ubuntu kernel: [    3.180597] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug  3 14:23:10 ubuntu kernel: [    3.180615] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Aug  3 14:23:10 ubuntu kernel: [    3.180635] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
Aug  3 14:23:10 ubuntu kernel: [    3.180684] usb usb6: configuration #1 chosen from 1 choice
Aug  3 14:23:10 ubuntu kernel: [    3.180699] hub 6-0:1.0: USB hub found
Aug  3 14:23:10 ubuntu kernel: [    3.180702] hub 6-0:1.0: 2 ports detected
Aug  3 14:23:10 ubuntu kernel: [    3.180728] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug  3 14:23:10 ubuntu kernel: [    3.180734] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug  3 14:23:10 ubuntu kernel: [    3.180752] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Aug  3 14:23:10 ubuntu kernel: [    3.180777] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
Aug  3 14:23:10 ubuntu kernel: [    3.180829] usb usb7: configuration #1 chosen from 1 choice
Aug  3 14:23:10 ubuntu kernel: [    3.180844] hub 7-0:1.0: USB hub found
Aug  3 14:23:10 ubuntu kernel: [    3.180848] hub 7-0:1.0: 2 ports detected
Aug  3 14:23:10 ubuntu kernel: [    3.180875] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug  3 14:23:10 ubuntu kernel: [    3.180881] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug  3 14:23:10 ubuntu kernel: [    3.180898] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Aug  3 14:23:10 ubuntu kernel: [    3.180917] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
Aug  3 14:23:10 ubuntu kernel: [    3.180967] usb usb8: configuration #1 chosen from 1 choice
Aug  3 14:23:10 ubuntu kernel: [    3.180981] hub 8-0:1.0: USB hub found
Aug  3 14:23:10 ubuntu kernel: [    3.180984] hub 8-0:1.0: 2 ports detected
Aug  3 14:23:10 ubuntu kernel: [    3.181011] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Aug  3 14:23:10 ubuntu kernel: [    3.181017] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Aug  3 14:23:10 ubuntu kernel: [    3.181034] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 9
Aug  3 14:23:10 ubuntu kernel: [    3.181054] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000f900
Aug  3 14:23:10 ubuntu kernel: [    3.181104] usb usb9: configuration #1 chosen from 1 choice
Aug  3 14:23:10 ubuntu kernel: [    3.181117] hub 9-0:1.0: USB hub found
Aug  3 14:23:10 ubuntu kernel: [    3.181121] hub 9-0:1.0: 2 ports detected
Aug  3 14:23:10 ubuntu kernel: [    3.181173] PNP: No PS/2 controller found. Probing ports directly.
Aug  3 14:23:10 ubuntu kernel: [    3.214560] Failed to disable AUX port, but continuing anyway... Is this a SiS?
Aug  3 14:23:10 ubuntu kernel: [    3.214561] If AUX port is really absent please use the 'i8042.noaux' option.
Aug  3 14:23:10 ubuntu kernel: [    3.459818] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug  3 14:23:10 ubuntu kernel: [    3.459864] mice: PS/2 mouse device common for all mice
Aug  3 14:23:10 ubuntu kernel: [    3.459922] rtc_cmos 00:04: RTC can wake from S4
Aug  3 14:23:10 ubuntu kernel: [    3.459942] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Aug  3 14:23:10 ubuntu kernel: [    3.459965] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Aug  3 14:23:10 ubuntu kernel: [    3.460038] device-mapper: uevent: version 1.0.3
Aug  3 14:23:10 ubuntu kernel: [    3.460090] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Aug  3 14:23:10 ubuntu kernel: [    3.460200] device-mapper: multipath: version 1.1.0 loaded
Aug  3 14:23:10 ubuntu kernel: [    3.460202] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug  3 14:23:10 ubuntu kernel: [    3.460426] cpuidle: using governor ladder
Aug  3 14:23:10 ubuntu kernel: [    3.460428] cpuidle: using governor menu
Aug  3 14:23:10 ubuntu kernel: [    3.460653] TCP cubic registered
Aug  3 14:23:10 ubuntu kernel: [    3.460729] NET: Registered protocol family 10
Aug  3 14:23:10 ubuntu kernel: [    3.461019] lo: Disabled Privacy Extensions
Aug  3 14:23:10 ubuntu kernel: [    3.461194] NET: Registered protocol family 17
Aug  3 14:23:10 ubuntu kernel: [    3.462669] registered taskstats version 1
Aug  3 14:23:10 ubuntu kernel: [    3.463204]   Magic number: 6:543:383
Aug  3 14:23:10 ubuntu kernel: [    3.463208] usb usb1: hash matches
Aug  3 14:23:10 ubuntu kernel: [    3.463266] rtc_cmos 00:04: setting system clock to 2010-08-03 14:22:33 UTC (1280845353)
Aug  3 14:23:10 ubuntu kernel: [    3.463268] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug  3 14:23:10 ubuntu kernel: [    3.463269] EDD information not available.
Aug  3 14:23:10 ubuntu kernel: [    3.489200] ata4: SATA link down (SStatus 0 SControl 300)
Aug  3 14:23:10 ubuntu kernel: [    3.499900] ata3: SATA link down (SStatus 0 SControl 300)
Aug  3 14:23:10 ubuntu kernel: [    3.825055] usb 3-2: new full speed USB device using uhci_hcd and address 2
Aug  3 14:23:10 ubuntu kernel: [    3.945611] ata2.00: SATA link down (SStatus 0 SControl 300)
Aug  3 14:23:10 ubuntu kernel: [    3.945623] ata2.01: SATA link down (SStatus 0 SControl 300)
Aug  3 14:23:10 ubuntu kernel: [    3.984869] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug  3 14:23:10 ubuntu kernel: [    3.984881] ata1.01: SATA link down (SStatus 0 SControl 300)
Aug  3 14:23:10 ubuntu kernel: [    4.001459] usb 3-2: configuration #1 chosen from 1 choice
Aug  3 14:23:10 ubuntu kernel: [    4.005006] ata1.00: ATAPI: HL-DT-ST BDDVDRW CH08LS10, 2.00, max UDMA/133
Aug  3 14:23:10 ubuntu kernel: [    4.044968] ata1.00: configured for UDMA/133
Aug  3 14:23:10 ubuntu kernel: [    4.052221] scsi 0:0:0:0: CD-ROM            HL-DT-ST BDDVDRW CH08LS10 2.00 PQ: 0 ANSI: 5
Aug  3 14:23:10 ubuntu kernel: [    4.057865] sr0: scsi3-mmc drive: 78x/78x writer dvd-ram cd/rw xa/form2 cdda tray
Aug  3 14:23:10 ubuntu kernel: [    4.057867] Uniform CD-ROM driver Revision: 3.20
Aug  3 14:23:10 ubuntu kernel: [    4.057940] sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug  3 14:23:10 ubuntu kernel: [    4.057977] Freeing unused kernel memory: 876k freed
Aug  3 14:23:10 ubuntu kernel: [    4.058114] Write protecting the kernel read-only data: 7680k
Aug  3 14:23:10 ubuntu kernel: [    4.068447] udev: starting version 151
Aug  3 14:23:10 ubuntu kernel: [    4.083008] Floppy drive(s): fd0 is 1.44M
Aug  3 14:23:10 ubuntu kernel: [    4.089085] vga16fb: mapped to 0xffff8800000a0000
Aug  3 14:23:10 ubuntu kernel: [    4.089127] fb0: VGA16 VGA frame buffer device
Aug  3 14:23:10 ubuntu kernel: [    4.090096] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Aug  3 14:23:10 ubuntu kernel: [    4.090113] r8169 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  3 14:23:10 ubuntu kernel: [    4.090586] pata_jmicron 0000:05:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug  3 14:23:10 ubuntu kernel: [    4.090656] eth0: RTL8168d/8111d at 0xffffc90000676000, 6c:f0:49:e4:f0:25, XID 083000c0 IRQ 36
Aug  3 14:23:10 ubuntu kernel: [    4.091394] scsi4 : pata_jmicron
Aug  3 14:23:10 ubuntu kernel: [    4.091455] scsi5 : pata_jmicron
Aug  3 14:23:10 ubuntu kernel: [    4.091836] pata_it8213 0000:08:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  3 14:23:10 ubuntu kernel: [    4.092135] ata5: PATA max UDMA/100 cmd 0xbf00 ctl 0xbe00 bmdma 0xbb00 irq 17
Aug  3 14:23:10 ubuntu kernel: [    4.092138] ata6: PATA max UDMA/100 cmd 0xbd00 ctl 0xbc00 bmdma 0xbb08 irq 17
Aug  3 14:23:10 ubuntu kernel: [    4.094774] scsi6 : pata_it8213
Aug  3 14:23:10 ubuntu kernel: [    4.094836] scsi7 : pata_it8213
Aug  3 14:23:10 ubuntu kernel: [    4.094864] ata7: PATA max UDMA/66 cmd 0x9f00 ctl 0x9e00 bmdma 0x9b00 irq 16
Aug  3 14:23:10 ubuntu kernel: [    4.094866] ata8: DUMMY
Aug  3 14:23:10 ubuntu kernel: [    4.096093] Initializing USB Mass Storage driver...
Aug  3 14:23:10 ubuntu kernel: [    4.096187] scsi8 : SCSI emulation for USB Mass Storage devices
Aug  3 14:23:10 ubuntu kernel: [    4.096251] usbcore: registered new interface driver usb-storage
Aug  3 14:23:10 ubuntu kernel: [    4.096253] USB Mass Storage support registered.
Aug  3 14:23:10 ubuntu kernel: [    4.098620] ahci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  3 14:23:10 ubuntu kernel: [    4.125329] ahci 0000:05:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Aug  3 14:23:10 ubuntu kernel: [    4.125332] ahci 0000:05:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Aug  3 14:23:10 ubuntu kernel: [    4.125424] scsi9 : ahci
Aug  3 14:23:10 ubuntu kernel: [    4.125465] scsi10 : ahci
Aug  3 14:23:10 ubuntu kernel: [    4.125517] ata9: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe100 irq 16
Aug  3 14:23:10 ubuntu kernel: [    4.125520] ata10: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe180 irq 16
Aug  3 14:23:10 ubuntu kernel: [    4.129641] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Aug  3 14:23:10 ubuntu kernel: [    4.129655] r8169 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Aug  3 14:23:10 ubuntu kernel: [    4.130099] eth1: RTL8168d/8111d at 0xffffc90000626000, 6c:f0:49:e4:f0:27, XID 083000c0 IRQ 37
Aug  3 14:23:10 ubuntu kernel: [    4.130302] FDC 0 is a post-1991 82077
Aug  3 14:23:10 ubuntu kernel: [    4.274526] usb 9-2: new low speed USB device using uhci_hcd and address 2
Aug  3 14:23:10 ubuntu kernel: [    4.455888] usb 9-2: configuration #1 chosen from 1 choice
Aug  3 14:23:10 ubuntu kernel: [    4.464862] usbcore: registered new interface driver hiddev
Aug  3 14:23:10 ubuntu kernel: [    4.464942] usbcore: registered new interface driver usbhid
Aug  3 14:23:10 ubuntu kernel: [    4.464944] usbhid: v2.6:USB HID core driver
Aug  3 14:23:10 ubuntu kernel: [    4.464966] ata9: SATA link down (SStatus 0 SControl 300)
Aug  3 14:23:10 ubuntu kernel: [    4.467459] ata10: SATA link down (SStatus 0 SControl 300)
Aug  3 14:23:10 ubuntu kernel: [    4.497995] ohci1394 0000:08:07.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug  3 14:23:10 ubuntu kernel: [    4.513896] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb9/9-2/9-2:1.0/input/input3
Aug  3 14:23:10 ubuntu kernel: [    4.513937] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.3-2/input0
Aug  3 14:23:10 ubuntu kernel: [    4.544755] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
Aug  3 14:23:10 ubuntu kernel: [    4.545072] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb9/9-2/9-2:1.1/input/input4
Aug  3 14:23:10 ubuntu kernel: [    4.545142] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.3-2/input1
Aug  3 14:23:10 ubuntu kernel: [    4.566738] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fb7ff000-fb7ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug  3 14:23:10 ubuntu kernel: [    4.618985] Console: switching to colour frame buffer device 80x30
Aug  3 14:23:10 ubuntu kernel: [    4.947585] xor: automatically using best checksumming function: generic_sse
Aug  3 14:23:10 ubuntu kernel: [    4.996265]    generic_sse: 10727.600 MB/sec
Aug  3 14:23:10 ubuntu kernel: [    4.996266] xor: using function: generic_sse (10727.600 MB/sec)
Aug  3 14:23:10 ubuntu kernel: [    4.997789] device-mapper: dm-raid45: initialized v0.2594b
Aug  3 14:23:10 ubuntu kernel: [    6.564436] aufs 2-standalone.tree-20091207
Aug  3 14:23:10 ubuntu kernel: [    6.683475] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Aug  3 14:23:10 ubuntu kernel: [    9.088498] scsi 8:0:0:0: Direct-Access     Brother  MFC-240C         1.00 PQ: 0 ANSI: 2
Aug  3 14:23:10 ubuntu kernel: [    9.088801] sd 8:0:0:0: Attached scsi generic sg1 type 0
Aug  3 14:23:10 ubuntu kernel: [    9.188394] sd 8:0:0:0: [sda] Attached SCSI removable disk
Aug  3 14:23:12 ubuntu kernel: [   42.039921] udev: starting version 151
Aug  3 14:23:15 ubuntu kernel: [   45.357301] r8169: eth0: link up
Aug  3 14:23:15 ubuntu kernel: [   45.357306] r8169: eth0: link up
Aug  3 14:23:15 ubuntu kernel: [   45.364442] r8169: eth1: link down
Aug  3 14:23:15 ubuntu kernel: [   45.364915] ADDRCONF(NETDEV_UP): eth1: link is not ready
Aug  3 14:23:15 ubuntu kernel: [   45.711112] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Aug  3 14:23:15 ubuntu kernel: [   45.711146] xhci_hcd 0000:04:00.0: xHCI Host Controller
Aug  3 14:23:15 ubuntu kernel: [   45.711197] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 10
Aug  3 14:23:15 ubuntu kernel: [   45.711340] xhci_hcd 0000:04:00.0: irq 19, io mem 0xfbefe000
Aug  3 14:23:15 ubuntu kernel: [   45.711380] usb usb10: config 1 interface 0 altsetting 0 endpoint 0x81 has no SuperSpeed companion descriptor
Aug  3 14:23:15 ubuntu kernel: [   45.711445] usb usb10: configuration #1 chosen from 1 choice
Aug  3 14:23:15 ubuntu kernel: [   45.711478] hub 10-0:1.0: USB hub found
Aug  3 14:23:15 ubuntu kernel: [   45.711483] hub 10-0:1.0: 4 ports detected
Aug  3 14:23:16 ubuntu kernel: [   46.383893] parport_pc 00:09: reported by Plug and Play ACPI
Aug  3 14:23:16 ubuntu kernel: [   46.383939] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Aug  3 14:23:16 ubuntu kernel: [   46.837309] ppdev: user-space parallel port driver
Aug  3 14:23:17 ubuntu kernel: [   47.418299] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x01AB
Aug  3 14:23:17 ubuntu kernel: [   47.418319] usbcore: registered new interface driver usblp
Aug  3 14:23:18 ubuntu kernel: [   48.522263] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug  3 14:23:18 ubuntu kernel: [   48.823569] hda_codec: ALC889: BIOS auto-probing.
Aug  3 14:23:18 ubuntu kernel: [   48.824990] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
Aug  3 14:23:18 ubuntu kernel: [   48.832787] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug  3 14:23:24 ubuntu kernel: [   54.861444] lp0: using parport0 (interrupt-driven).
Aug  3 14:23:27 ubuntu kernel: [   57.612531] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  3 18:23:40 ubuntu kernel: [   61.798139] usb 3-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Aug  3 18:24:15 ubuntu kernel: [   97.290044] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Aug  3 18:24:33 ubuntu pulseaudio[2866]: ratelimit.c: 29 events suppressed
Aug  3 18:25:37 ubuntu kernel: [  178.805152] usb 3-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

---

### Post by JustinR on 2010-08-03
> **MindGizmoWizard said:**
> GParted does the same as the Ubuntu Install: everything's just empty.

I opened the messages with gedit and saved it on desktop. Here's the text:
...


Thanks, okay, bootup into the Live-CD again, go to **Applications > Accessories > Terminal**. And type this in:
```

sudo apt-get remove dmraid

```
Enter in your password and when it is done, go to the Desktop and double click "Install Ubuntu" and see what happens.

---

### Post by MindGizmoWizard on 2010-08-03
Well, it didn't ask me for a password... It just asked "Do you want to continue? (Y/N)"

Of course, I said yes... then it did a bunch of stuff. Then went back to the command prompt.

I tried the install... and it did the same thing as it did the first time. Still stuck at step 4.

---

### Post by JustinR on 2010-08-03
> **MindGizmoWizard said:**
> Well, it didn't ask me for a password... It just asked "Do you want to continue? (Y/N)"

Of course, I said yes... then it did a bunch of stuff. Then went back to the command prompt.

I tried the install... and it did the same thing as it did the first time. Still stuck at step 4.

Okay - sorry it didn't work!

On to the next step:
Go into your BIOS (when you see your computer logo press the key that shows up next to 'BIOS' or 'Setup, etc. Its usually F2 for Dell's, but you could try ESC, F12.

Once your in your BIOS, go down to Hard Drive connector, or if that doesn't exist, look through the hard drive settings until you see information on "IDE" and "SATA, or even "ACHI". Change that settings from "SATA" to "IDE".

---

### Post by MindGizmoWizard on 2010-08-03
I know my HD is SATA...
Is that going to be a problem?

(BTW here's what it added in text)

Aug  3 14:52:50 ubuntu ubiquity[4212]: Ubiquity 2.2.24
Aug  3 14:52:52 ubuntu ubiquity[4212]: switched to page language
Aug  3 14:52:53 ubuntu ubiquity[4212]: switched to page language
Aug  3 14:52:56 ubuntu localechooser: info: Language = 'en'
Aug  3 14:52:57 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Aug  3 14:52:57 ubuntu localechooser: info: Set debian-installer/language = 'en'
Aug  3 14:52:57 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Aug  3 14:52:57 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Aug  3 14:52:57 ubuntu localechooser: info: Default country = 'US'
Aug  3 14:52:57 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Aug  3 14:52:57 ubuntu localechooser: info: Set debian-installer/country = 'US'
Aug  3 14:52:57 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Aug  3 14:52:57 ubuntu localechooser: info: Selected locale (debian-installer/locale) = 'en_US.UTF-8'
Aug  3 14:52:57 ubuntu ubiquity[4212]: Step_before = stepLanguage
Aug  3 18:53:07 ubuntu clock-setup: Tue Aug  3 18:53:07 UTC 2010
Aug  3 18:53:07 ubuntu clock-setup: rdate: adjust local clock by 14408.875986 seconds
Aug  3 18:53:09 ubuntu ubiquity[4212]: switched to page timezone
Aug  3 18:53:10 ubuntu localechooser: info: Locale has been preseeded to en_CA.UTF-8
Aug  3 18:53:10 ubuntu localechooser: info: Set localechooser/languagelist = 'en'
Aug  3 18:53:10 ubuntu localechooser: info: Set debian-installer/country = 'CA'
Aug  3 18:53:10 ubuntu localechooser: info: Set debian-installer/locale = 'en_CA.UTF-8'
Aug  3 18:53:10 ubuntu localechooser: info: Language = 'en'
Aug  3 18:53:10 ubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Aug  3 18:53:10 ubuntu localechooser: info: Set debian-installer/language = 'en'
Aug  3 18:53:10 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Aug  3 18:53:10 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Aug  3 18:53:10 ubuntu localechooser: info: Default country = 'US'
Aug  3 18:53:10 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Aug  3 18:53:10 ubuntu localechooser: info: Set debian-installer/country = 'CA'
Aug  3 18:53:10 ubuntu localechooser: info: Set debian-installer/locale = 'en_CA.UTF-8'
Aug  3 18:53:10 ubuntu localechooser: info: Selected locale (debian-installer/locale) = 'en_CA.UTF-8'
Aug  3 18:53:11 ubuntu kernel: [ 1831.511630] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Aug  3 18:53:11 ubuntu kernel: [ 1831.512997] SGI XFS Quota Management subsystem
Aug  3 18:53:11 ubuntu kernel: [ 1831.582531] JFS: nTxBlock = 8192, nTxLock = 65536
Aug  3 18:53:11 ubuntu kernel: [ 1831.683003] NTFS driver 2.1.29 [Flags: R/O MODULE].
Aug  3 18:53:11 ubuntu kernel: [ 1831.848254] QNX4 filesystem 0.2.3 registered.
Aug  3 18:53:12 ubuntu kernel: [ 1832.127219] Btrfs loaded
Aug  3 18:53:12 ubuntu ubiquity[4212]: Step_before = stepLocation
Aug  3 18:53:12 ubuntu ubiquity[4212]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Aug  3 18:53:12 ubuntu ubiquity[4212]: switched to page console_setup
Aug  3 18:53:18 ubuntu ubiquity[4212]: log-output -t ubiquity setxkbmap -model pc105 -layout ca -option  -option lv3:ralt_switch
Aug  3 18:53:18 ubuntu ubiquity[4212]: switched to page console_setup
Aug  3 18:53:21 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Aug  3 18:53:21 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Aug  3 18:53:21 ubuntu ubiquity[4212]: log-output -t ubiquity setxkbmap -model pc105 -layout ca -option 
Aug  3 18:53:21 ubuntu ubiquity[4212]: Step_before = stepKeyboardConf
Aug  3 18:53:46 ubuntu ubiquity[4212]: switched to page partman
Aug  3 18:53:46 ubuntu ubiquity[4212]: switched to page partman
Aug  3 18:56:20 ubuntu ubiquity[4212]: switched to page partman
Aug  3 18:56:23 ubuntu ubiquity[4212]: switched to page partman
Aug  3 18:56:25 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Aug  3 18:56:25 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat

---

### Post by JustinR on 2010-08-03
> **MindGizmoWizard said:**
> I know my HD is SATA...
Is that going to be a problem?

(BTW here's what it added in text)

...

Thanks for the added information - and yes sometimes SATA could be the problem on a few computers - so try switching it to IDE.

---

### Post by MindGizmoWizard on 2010-08-03
Well, everything in my BIOS says "IDE" where it could say it. It was already this way...

...so could it be anything else?

(My HD is a WDC WD1002FAEX-00Z3A0 ATA)

---

### Post by JustinR on 2010-08-03
> **MindGizmoWizard said:**
> Well, everything in my BIOS says "IDE" where it could say it. It was already this way...

...so could it be anything else?

(My HD is a WDC WD1002FAEX-00Z3A0 ATA)

I hate to second guess - but, Are you sure IDE is actually selected? Almost 100% of the time IDE's are compatible with almost any OS. But if it is - we can try another solution.

Edit: I have go to - I'll be back in a few hours!

---

### Post by MindGizmoWizard on 2010-08-03
Here are a few things from my BIOS:

             (Standard CMOS Features)
  IDE Channel 0 Master [HL-DT-ST  BDDVDRW CH0...]
  IDE Channel 0 Slave [None]
  ...
  IDE Channel 6 Master [WDC WD1002FAEX-00Z3A...]
  IDE Channel 6 Slave [None]
  ...
   
  (Integrated Peripherals)
  eXtreme Hard Drive (XHD)  [Disabled]
  PCH SATA Control Mode [IDE]
  SATA Port0-3 Native Mode [Enabled]
  USB Controllers [Enabled]
  USB Legacy Function [Enabled]
  USB Storage Function [Enabled]
  Turbo SATA3/USB3.0 [Auto]
  Azalia Codec [Auto]
  Onboard H/W 1394 [Enabled]
  Onboard H/W LAN1 [Enabled]
  Onboard H/W LAN2 [Enabled]
  Green LAN [Disabled]
  SMART LAN1 [Press Enter]
  SMART LAN2 [Press Enter]
  Onboard LAN1 Boot ROM [Disabled]
  Onboard LAN2 Boot ROM [Disabled]
  Onboard USB 3.0 Controller  [Enabled]
  Onboard IDE Controller [Enabled]
  eSATA Controller [Enabled]
  eSATA Ctrl Mode [IDE]
  GSATA Controller [Enabled]
  GSATA Ctrl Mode [IDE]
  GSATA RAID Configuration [Press  Enter]
  Onboard Serial Port 1 [3F8/IRQ4]
  Onboard Parallel Port [378/IRQ7]
  Parallel Port Mode [SPP]

---

### Post by TNT1 on 2010-08-03
I once tried Win7RC in a dual boot, it completely killed GRUB. I heard from guys in local community that it was common. Dunno if that helps, cause my solution was that windows messed up and I didn't try 7 again.

---

### Post by MindGizmoWizard on 2010-08-03
Win7RC?
Windows 7... RC? What does that mean?

Anyways, I keep in mind that this may be in vain, but I want to keep trying... only I have no idea what to try.

---

### Post by Elmer Fudd on 2010-08-03
(R)elease (C)andidate. A pre-release version of a piece of software- in this case Windows 7

---

### Post by MindGizmoWizard on 2010-08-03
Oh...

Isn't it possible then that a later version could work? I have Windows 7 Professionnal... 
<hope>

---

### Post by Elmer Fudd on 2010-08-03
Absolutely. 
Like many others, I have Win7 running in Dual-boot. I don't believe that Win7 is the problem.
You have people here who are far more knowledgable than I who are trying to help. 
But while you are waiting for them to get back to you, I would still like to know what happens when you run GParted from the live CD.  Does it see the 1tb drive at all?
Also, while rare, I have had bad install CDs and had to re download/burn the live CD.
Just grabbing a straws here while you wait for the experts.

---

### Post by MindGizmoWizard on 2010-08-03
It doesn't see anything at all, exactly like the Ubuntu 10.04 LTS installer. The window is completely empty.

---

### Post by Elmer Fudd on 2010-08-03
You noted in you BIOS
"GSATA RAID Configuration [Press Enter]"

Did you "press enter" to look at the raid config?

(Don't forget to exit the Bios setup with "abandon changes" so you don't accidentally mess up your win7 install.)

Is Raid enabled? It shouldn't be with a single drive. 
I have seen a few threads where Raid was a problem.

---

### Post by MindGizmoWizard on 2010-08-03
Nope, I confirm that there is no RAID whatsoever.
(Anyway, isn't that when you use several HDs? I only have one...)

---

### Post by Elmer Fudd on 2010-08-03
Would you consider downloading an trying another distro. Maybe non-Debian just to see if has the same problem?

[http://fedoraproject.org/get-fedora](http://fedoraproject.org/get-fedora)

---

### Post by MindGizmoWizard on 2010-08-03
I'd rather not, but I'll do it if all else fails...

---

### Post by Elmer Fudd on 2010-08-04
I keep running into posts where RAID was the problem- even in systems where RAID was not active. Was RAID ever configured in this computer or with this harddrive in any computer.

---

### Post by MindGizmoWizard on 2010-08-04
Yeah, every other post I've seen about running Windows 7 with Ubuntu was about RAID.

However, every part on this computer is brand new, and I did not know about RAID at all. (I barely know about it now)

Here's what I have:
Mobo: Gigabyte P55A-UD4P ATX LGA1156 P55 DDR3 2PCI-E RAID GBLAN CrossFireX SLI USB3.0 SATA3 Motherboard
CPU: Intel Core i7 875K Quad Core LGA1156 2.93GHZ Hyperthreading 8MB Cache Unlocked Processor
GPU: XFX HD-587X-ZNDC Radeon HD 5870 (Cypress XT) XXX Edition 1GB 256-bit DDR5 PCI Express 2.1 x16 HDCP Ready CrossFireX Support Video Card w/ Eyefinity
HD: Western Digital Caviar Black 1TB SATA3 6GB/S 7200RPM 64MB Cache 3.5IN Dual Proc Hard Drive OEM
Case: Antec Twelve Hundred 1200 Full Tower Gamer Case ATX 12 Drive Bay No PS Top USB2.0 1394 Audio eSATA

Any other relevant info?

---

### Post by eaglemob on 2010-08-04
> **MindGizmoWizard said:**
> Yeah, every other post I've seen about running Windows 7 with Ubuntu was about RAID.

However, every part on this computer is brand new, and I did not know about RAID at all. (I barely know about it now)

?

Well i do not understand your problem.
Are you trying to install win7+ubuntu on a raid, or win7+ubuntu on NON raid ?

---

### Post by MindGizmoWizard on 2010-08-04
I'm trying to install Ubuntu on my computer which has Windows 7.
I don't have RAID or anything.
My problem is that Ubuntu does not seem to recognize the existence of my HD.

---

### Post by Elmer Fudd on 2010-08-04
MGW,

If the experts are taking a break, are you ready to find out if it is a Ubuntu/Debian problem?

Just download burn and run live CD. 
You don't have to install it. Just find out if it sees the drive.

[http://fedoraproject.org/get-fedora](http://fedoraproject.org/get-fedora)

---

### Post by MindGizmoWizard on 2010-08-04
Fedora gives me the same treatment. No devices detected.

It's so weird, Windows 7 sees all of it just fine. I have a partition for Windows 7 itself, a partition for the C: stuff that's about 250 Gb, a Data Storage partition that's 500 Gb and about 250 Gb of unallocated space.

...Maybe it's because I partitioned the HD with Windows 7's software?

---

### Post by VastOne on 2010-08-04
What we need (I think) is you to boot with the LiveCD and run Gparted and take a screen shot of that and post it here so that we can get a view of what Ubuntu sees in this hard drive.

---

### Post by Elmer Fudd on 2010-08-04
> **MindGizmoWizard said:**
> Fedora gives me the same treatment. No devices detected.

It's so weird, Windows 7 sees all of it just fine. I have a partition for Windows 7 itself, a partition for the C: stuff that's about 250 Gb, a Data Storage partition that's 500 Gb and about 250 Gb of unallocated space.

...Maybe it's because I partitioned the HD with Windows 7's software?

If you download SuperGrub, burn and boot from it, and it does not see the Win7 boot info then I would have to believe that the Win7 partioning is doing something non-standard.

[http://prdownload.berlios.de/supergrub/super_grub_disk_hybrid-1.98s1.iso](http://prdownload.berlios.de/supergrub/super_grub_disk_hybrid-1.98s1.iso)

I haven't played with the win7 partitioning software. Can you print, from Win7, a summary or show an image of what it has configured?

---

### Post by MindGizmoWizard on 2010-08-04
Here's the GParted result.
As I said. There's nothing.

I reeeeeeeeeeeeeeally hope I don't have to install Windows 7 all over again just to get Ubuntu, I spent several days redownloading stuff and my internets might bust...

I'll try your program and see what happens.

EDIT: WHAT?? WHAT THE HELL?
This is really annoying!
Now even the damn screenshots won't work...
Let's try direct link:
[IMG]http://i231.photobucket.com/albums/ee304/mindgizmowizard/Screenshot.png[/IMG]

---

### Post by ronparent on 2010-08-05
I note you are using a SATA3 MB. Is your drive plugged into a SATA2 or SATA3 port? And is your drive SATA2 or SATA3. I've heard of instances where a SATA2 drive isn't recognized by Ubuntu when its plugged into a a SATA3 port.

---

### Post by MindGizmoWizard on 2010-08-05
My HD is a:
Western Digital Caviar Black 1TB SATA3 6GB/S 7200RPM 64MB Cache 3.5IN Dual Proc Hard Drive OEM

There's a SATA3 in there so I'm going to assume it's a SATA3.

And it was indeed plugged into SATA3. We made sure to put the HD there since my mobo has a grand total of 2 SATA3 slots.

:(

---

### Post by SHO_ONE on 2010-08-06
I'm extremly new to the whole community and Ubuntu in general. I'm not a novice when it comes to computers and feel I can hold my own; however when trying to install Ubuntu 10.04 on my Win 7 laptop, I'm only presented with 1 option.... to install over Windows 7 (64bit AMD) completely. 
 
Yes I've created a partion and when I get to step 4 of 7 or 8 I can see the partition up at the top of the menu, but I have no option to install side by side or to install to the greatest unalocated space available. What am I doint wrong here guys..... any assistance would be greatly appreciated.
 
Once that's done.... I'll move on to why I can't simply update flash

---

### Post by ronparent on 2010-08-06
MindGizmoWizard - I hate to say it, but, it must be a bug. I appears, that in least some circumstances, Ubuntu 10.04 doesn't recognize the SATA 3 port? Have you considered submitting a bug report?

SHO_ONE- You should start you own thread because you don't seem to be addressing the same problem. If you have actually pre-created a target partition to install to, you need to use the third option in step 4 (select your own partition to install to). You would also need to make sure you have created a 'swap' partition (not absolutely necessary but wiser).

---

### Post by Elmer Fudd on 2010-08-06
MGW,
Did you do a boottime chkdsk/f on the win7 partiion before you started the 10.04 install?
Have you tried to see what supergrub sees yet?

Hoping that it is not a bug.

---

### Post by YesWeCan on 2010-08-06
> **MindGizmoWizard said:**
> Well, everything in my BIOS says "IDE" where it could say it. It was already this way...

...so could it be anything else?

(My HD is a WDC WD1002FAEX-00Z3A0 ATA)
Someone got SATA3 working with SuSE: [http://www.linuxforums.org/forum/suse-linux-help/164870-solved-sata-3-0-support-opensuse-11-2-a.html](http://www.linuxforums.org/forum/suse-linux-help/164870-solved-sata-3-0-support-opensuse-11-2-a.html)

---

### Post by mikakukk on 2010-11-06
Hello!

I have same kind of problem, Ubuntu 10.10 live-cd (and 10.04) doesn't see my hard drives. I have two WD CAVIAR BLACK 1TB SATA3 7200RPM 64MB (WDC WD1002FAEX-00Z3A0) hard drives. One has Win 7 64-bit installed on it, another one is empty and I want to install Ubuntu 10.10 64-bit on it.

When hard drives are installed into motherboards SATA 3 port, Ubuntu doesn't recognize them. But if I'll attach them into normal SATA port, Ubuntu recognizes hard drives. My motherboard is Asus P7P55D-E.

If I'll attach both hard drives into normal SATA port, I'll have to install Win 7 again.. I could attach second hd into normal SATA port and then install Ubuntu, but I think that then I would not be able to choose between Ubuntu and Windows, when starting computer.

---

