---
title: "Acer C720 Chromebook and Ubuntu"
date: 2014-01-04
forum: Installation &amp; Upgrades
---

### Post by makitso on 2014-01-04
I have been thinking about getting the subject Acer and installing Ubuntu on it.  With the limited 16G SSD there is not a lot of room so I might upgrade to a 64G SSD.  
My questions are, 

if you use ChrUbuntu, is it better to dual boot (probably what I would do for performance ) or boot to Chrome and then hot switch to ubuntu? 
Will the system support the Unity or Gnome desktop?
I have been testing 14.04 and its very stable and efficient.  How might one install this and has anyone done this?
I would need the keyboard trackpad to work. 

Rob
[h=3][/h]

---

### Post by TNFrank on 2014-01-13
Kind of in the same vein, I just picked up an Acer Aspire One ZG5 AOA110 with an Intel Atom N270, 1.6GHz processor that was set up with Windows XP so it has 1GB of RAM instead of the "stock" 512MB. It still has the slow 8GB SSD in it(I have a KingSpec 32GB on order, should make it a lot faster) and I'm running Ubuntu/GNOME 13.10 on it and it seems to run fine.  Not going to win any speed contests, checked it with hardinfo's CPU Blowfish benchmark and got a 16.68(my HP/Compaq nc6400 w/Core Duo 1.83GHz processor ranks a 9.28 in the same test, faster is better by the way.) but I hope that the new SSD and bumping the RAM up to it's full 1.5GB will help to speed it up a bit. 
I guess you have to be willing to give up a bit of performance for the convenience of having such a small, easy to carry "laptop".  Anyway, I'd give Ubuntu with GNOME 3 a try, if it works then great, if now then try some of the lighter DE's like XFCE or LXDE. ;)

---

### Post by JRV on 2014-01-29
I just installed Ubuntu 12.04 on my Acer C720 using ChrUbuntu.

Installation instructions: [http://chromeos-cr48.blogspot.fr/2013/05/chrubuntu-one-script-to-rule-them-all_31.html](http://chromeos-cr48.blogspot.fr/2013/05/chrubuntu-one-script-to-rule-them-all_31.html)

I gave Ubuntu 9 gig of the SSD.  The install and the extra programs I added take up 3 gig.
My stuff is stored on my desktop so storage is not a problem, but I will carry a large SD card with me just in case.
It's much faster than I expected, and it runs Ubuntu with Unity 2d very well in most cases, but there are some problems.

- There is no Delete key, you have to use the Backspace.

- ChrUbuntu configures one user whose username and password are "user".
  
- User Accounts under System Settings does not work, so I created a user for myself from the command line.
  I added my new user to the sudoers list and deleted the user "user".

- To run things like gparted, symantic, or the update manager I must start them form the command line with gksudo.

To answer your questions:

It does not dual boot.  When started it displays a message that says "OS verification is off" press <CTRL>-D or wait 30 seconds for it to boot.

Ubuntu 12.04 only runs Unity 2d I believe the newer versions will run the full Unity.  

The second time you run the"curl" command enter these parameters:
```

curl -L -O http://goo.gl/s9ryd; sudo bash s9ryd default dev

```

I've read that the trackpad does not work but mine does.
(Not fully tested, I use a mouse because I don't like trackpads.)

---

### Post by philinux on 2014-01-29
Moved to Installation & upgrades

---

### Post by robartist on 2014-02-25
I too have installed Ubuntu on my Chromebook Acer c720. It kind of works but there are some problems. The biggest problem is the touchpad which initially didn't two finger scroll. But then I started again and reinstalled and at the moment it does two finger scroll.
But... it has a habit of right clicking when I want a left click which is particularly annoying.

Also the software-center doesn't work properly, I can't download software from it. And sometimes programmes won't start by clicking on the icon so I have to start them from the terminal. And sometimes they don't stop so I have to stop them from the terminal.

But.... my major reason for all of this is that I am a pensioner (=not much money) and a cyclist (need lightweight small laptop) and I wanted a long battery life. So the £199 Acer c720 seemed like a good option for me. 

To be honest Chrome does most of what I want to do. The two things it cannot do are Skype (my friends won't move over to the Google equivalent) and Anki a programme that I am using to learn a foreign language. Both of these work fairly well on Ubuntu on my Chromebook.

If I could solve the left click right click problem I would be much happier though. At the moment I have to cart around a mouse with me, which I find inconvenient.

All the best

---

### Post by dorijan69 on 2014-04-18
Does anyone else have slow bootup times with c720?
This is my dmesg:

> [    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-24-generic (buildd@panlong) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 (Ubuntu 3.13.0-24.46-generic 3.13.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=e752f3ab-e4c0-437a-a3f6-c2a4b9b1b7f1 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000002ffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000030000-0x000000000003ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000040000-0x000000000009e3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000000efffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000f00000-0x0000000000ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000001000000-0x000000007bf79fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007bf7a000-0x000000007e9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f3ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed84000-0x00000000fed84fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000001005fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Acer Peppy, BIOS          10/29/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x100600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-back
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7F80000000 write-back
[    0.000000]   1 base 007C800000 mask 7FFF800000 uncachable
[    0.000000]   2 base 007D000000 mask 7FFF000000 uncachable
[    0.000000]   3 base 007E000000 mask 7FFE000000 uncachable
[    0.000000]   4 base 00D0000000 mask 7FF0000000 write-combining
[    0.000000]   5 base 00FF800000 mask 7FFF800000 uncachable
[    0.000000]   6 base 0100000000 mask 7F00000000 write-back
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0x7bf7a max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x100400000-0x1005fffff]
[    0.000000]  [mem 0x100400000-0x1005fffff] page 2M
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1003fffff]
[    0.000000]  [mem 0x100000000-0x1003fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x00efffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x00dfffff] page 2M
[    0.000000]  [mem 0x00e00000-0x00efffff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x01000000-0x7bf79fff]
[    0.000000]  [mem 0x01000000-0x7bdfffff] page 2M
[    0.000000]  [mem 0x7be00000-0x7bf79fff] page 4k
[    0.000000] RAMDISK: [mem 0x35ba0000-0x36dc7fff]
[    0.000000] ACPI: RSDP 00000000000fdbb0 000024 (v02 CORE  )
[    0.000000] ACPI: XSDT 000000007bf840e0 000054 (v01 CORE   COREBOOT 00000000 CORE 00000000)
[    0.000000] ACPI: FACP 000000007bf88690 0000F4 (v03 CORE   COREBOOT 00000000 CORE 00000001)
[    0.000000] ACPI Error: Gpe0Block - 32-bit FADT register is too long (32 bytes, 256 bits) to convert to GAS struct - 255 bits max, truncating (20131115/tbfadt-202)
[    0.000000] ACPI: DSDT 000000007bf84250 004431 (v02 COREv4 COREBOOT 20110725 INTL 20090123)
[    0.000000] ACPI: FACS 000000007bf84210 000040
[    0.000000] ACPI: HPET 000000007bf88790 000038 (v01 CORE   COREBOOT 00000000 CORE 00000000)
[    0.000000] ACPI: APIC 000000007bf887d0 00005C (v01 CORE   COREBOOT 00000000 CORE 00000000)
[    0.000000] ACPI: MCFG 000000007bf88830 00003C (v01 CORE   COREBOOT 00000000 CORE 00000000)
[    0.000000] ACPI: SSDT 000000007bf89730 0008A0 (v02 CORE   COREBOOT 0000002A CORE 0000002A)
[    0.000000] ACPI: SSDT 000000007bf89fd0 00005C (v02 CORE   COREBOOT 0000002A CORE 0000002A)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000001005fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x1005fffff]
[    0.000000]   NODE_DATA [mem 0x1005f9000-0x1005fdfff]
[    0.000000]  [ffffea0000000000-ffffea00041fffff] PMD -> [ffff880079800000-ffff88007b9fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x1005fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0002ffff]
[    0.000000]   node   0: [mem 0x00040000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0x00efffff]
[    0.000000]   node   0: [mem 0x01000000-0x7bf79fff]
[    0.000000]   node   0: [mem 0x100000000-0x1005fffff]
[    0.000000] On node 0 totalpages: 508935
[    0.000000]   DMA zone: 59 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3725 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7870 pages used for memmap
[    0.000000]   DMA32 zone: 503674 pages, LIFO batch:31
[    0.000000]   Normal zone: 24 pages used for memmap
[    0.000000]   Normal zone: 1536 pages, LIFO batch:0
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 56
[    0.000000] PM: Registered nosave memory: [mem 0x00030000-0x0003ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x00f00000-0x00ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7bf7a000-0x7e9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7ea00000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf3ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf4000000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed83fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed84000-0xfed84fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed85000-0xffffffff]
[    0.000000] e820: [mem 0x7ea00000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff880100200000 s86336 r8192 d24256 u1048576
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 500961
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=e752f3ab-e4c0-437a-a3f6-c2a4b9b1b7f1 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 1899412K/2035740K available (7338K kernel code, 1138K rwdata, 3388K rodata, 1332K init, 1440K bss, 136328K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-1.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 8912896 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1396.801 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 2793.60 BogoMIPS (lpj=5587204)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000038] Security Framework initialized
[    0.000058] AppArmor: AppArmor initialized
[    0.000060] Yama: becoming mindful.
[    0.000360] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.000989] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.001268] Mount-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.001277] Mountpoint-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.001523] Initializing cgroup subsys memory
[    0.001530] Initializing cgroup subsys devices
[    0.001533] Initializing cgroup subsys freezer
[    0.001535] Initializing cgroup subsys blkio
[    0.001537] Initializing cgroup subsys perf_event
[    0.001540] Initializing cgroup subsys hugetlb
[    0.001589] CPU: Physical Processor ID: 0
[    0.001591] CPU: Processor Core ID: 0
[    0.002930] mce: CPU supports 7 MCE banks
[    0.002948] CPU0: Thermal monitoring enabled (TM1)
[    0.002963] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.002963] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.002963] tlb_flushall_shift: 6
[    0.003124] Freeing SMP alternatives memory: 32K (ffffffff81e6b000 - ffffffff81e73000)
[    0.004639] ACPI: Core revision 20131115
[    0.007608] ACPI: All ACPI Tables successfully acquired
[    0.009669] ftrace: allocating 28408 entries in 111 pages
[    0.028782] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068465] smpboot: CPU0: Intel(R) Celeron(R) 2955U @ 1.40GHz (fam: 06, model: 45, stepping: 01)
[    0.068474] TSC deadline timer enabled
[    0.071472] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.071483] ... version:                3
[    0.071484] ... bit width:              48
[    0.071486] ... generic registers:      8
[    0.071487] ... value mask:             0000ffffffffffff
[    0.071489] ... max period:             0000ffffffffffff
[    0.071490] ... fixed-purpose events:   3
[    0.071492] ... event mask:             00000007000000ff
[    0.073783] x86: Booting SMP configuration:
[    0.073787] .... node  #0, CPUs:      #1
[    0.088345] x86: Booted up 1 node, 2 CPUs
[    0.088349] smpboot: Total of 2 processors activated (5587.20 BogoMIPS)
[    0.088433] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.090471] devtmpfs: initialized
[    0.093324] EVM: security.selinux
[    0.093326] EVM: security.SMACK64
[    0.093327] EVM: security.ima
[    0.093329] EVM: security.capability
[    0.094398] pinctrl core: initialized pinctrl subsystem
[    0.094478] regulator-dummy: no parameters
[    0.094516] RTC time: 22:36:35, date: 04/18/14
[    0.094561] NET: Registered protocol family 16
[    0.094689] cpuidle: using governor ladder
[    0.094691] cpuidle: using governor menu
[    0.094744] ACPI: bus type PCI registered
[    0.094746] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.094805] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.094809] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.102648] PCI: Using configuration type 1 for base access
[    0.103725] bio: create slab <bio-0> at 0
[    0.103912] ACPI: Added _OSI(Module Device)
[    0.103915] ACPI: Added _OSI(Processor Device)
[    0.103917] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.103919] ACPI: Added _OSI(Processor Aggregator Device)
[    0.108542] ACPI: Interpreter enabled
[    0.108549] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.108555] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.108573] ACPI: (supports S0 S3 S4 S5)
[    0.108574] ACPI: Using IOAPIC for interrupt routing
[    0.108599] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.108768] ACPI: No dock devices found.
[    0.115797] ACPI: Power Resource [TNP0] (off)
[    0.115834] ACPI: Power Resource [TNP1] (on)
[    0.116357] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.116364] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.116413] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.116532] acpi PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cebff])
[    0.116538] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.116779] PCI host bridge to bus 0000:00
[    0.116783] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.116786] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.116788] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.116791] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.116793] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.116795] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.116798] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.116800] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.116802] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.116804] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.116807] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.116809] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.116811] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.116813] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.116816] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.116818] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
[    0.116820] pci_bus 0000:00: root bus resource [mem 0x7ea00001-0xfebfffff]
[    0.116823] pci_bus 0000:00: root bus resource [mem 0xfed40000-0xfed44fff]
[    0.116834] pci 0000:00:00.0: [8086:0a04] type 00 class 0x060000
[    0.116965] pci 0000:00:02.0: [8086:0a06] type 00 class 0x030000
[    0.116983] pci 0000:00:02.0: reg 0x10: [mem 0xe0000000-0xe03fffff 64bit]
[    0.116993] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.117001] pci 0000:00:02.0: reg 0x20: [io  0x1800-0x183f]
[    0.117124] pci 0000:00:03.0: [8086:0a0c] type 00 class 0x040300
[    0.117137] pci 0000:00:03.0: reg 0x10: [mem 0xe0510000-0xe0513fff 64bit]
[    0.117283] pci 0000:00:14.0: [8086:9c31] type 00 class 0x0c0330
[    0.117306] pci 0000:00:14.0: reg 0x10: [mem 0xe0500000-0xe050ffff 64bit]
[    0.117377] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.117442] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.117482] pci 0000:00:15.0: [8086:9c60] type 00 class 0x080102
[    0.117503] pci 0000:00:15.0: reg 0x10: [mem 0xe0518000-0xe0518fff]
[    0.117516] pci 0000:00:15.0: reg 0x14: [mem 0xe0519000-0xe0519fff]
[    0.117681] pci 0000:00:15.1: [8086:9c61] type 00 class 0x0c8000
[    0.117702] pci 0000:00:15.1: reg 0x10: [mem 0xe051a000-0xe051afff]
[    0.117714] pci 0000:00:15.1: reg 0x14: [mem 0xe051b000-0xe051bfff]
[    0.117876] pci 0000:00:15.2: [8086:9c62] type 00 class 0x0c8000
[    0.117897] pci 0000:00:15.2: reg 0x10: [mem 0xe051c000-0xe051cfff]
[    0.117909] pci 0000:00:15.2: reg 0x14: [mem 0xe051d000-0xe051dfff]
[    0.118080] pci 0000:00:1b.0: [8086:9c20] type 00 class 0x040300
[    0.118097] pci 0000:00:1b.0: reg 0x10: [mem 0xe0514000-0xe0517fff 64bit]
[    0.118173] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.118239] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.118273] pci 0000:00:1c.0: [8086:9c10] type 01 class 0x060400
[    0.118356] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.118466] pci 0000:00:1d.0: [8086:9c26] type 00 class 0x0c0320
[    0.118490] pci 0000:00:1d.0: reg 0x10: [mem 0xe051f800-0xe051fbff]
[    0.118595] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.118662] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.118700] pci 0000:00:1f.0: [8086:9c45] type 00 class 0x060100
[    0.118913] pci 0000:00:1f.2: [8086:9c03] type 00 class 0x010601
[    0.118932] pci 0000:00:1f.2: reg 0x10: [io  0x1860-0x1867]
[    0.118941] pci 0000:00:1f.2: reg 0x14: [io  0x1870-0x1873]
[    0.118950] pci 0000:00:1f.2: reg 0x18: [io  0x1868-0x186f]
[    0.118960] pci 0000:00:1f.2: reg 0x1c: [io  0x1874-0x1877]
[    0.118969] pci 0000:00:1f.2: reg 0x20: [io  0x1840-0x185f]
[    0.118978] pci 0000:00:1f.2: reg 0x24: [mem 0xe051f000-0xe051f7ff]
[    0.119022] pci 0000:00:1f.2: PME# supported from D3hot
[    0.119113] pci 0000:00:1f.3: [8086:9c22] type 00 class 0x0c0500
[    0.119130] pci 0000:00:1f.3: reg 0x10: [mem 0xe051fc00-0xe051fcff 64bit]
[    0.119155] pci 0000:00:1f.3: reg 0x20: [io  0x0400-0x041f]
[    0.119269] pci 0000:00:1f.6: [8086:9c24] type 00 class 0x118000
[    0.119303] pci 0000:00:1f.6: reg 0x10: [mem 0xe051e000-0xe051efff 64bit]
[    0.119569] pci 0000:01:00.0: [168c:0034] type 00 class 0x028000
[    0.119595] pci 0000:01:00.0: reg 0x10: [mem 0xe0400000-0xe047ffff 64bit]
[    0.119656] pci 0000:01:00.0: reg 0x30: [mem 0xe0480000-0xe048ffff pref]
[    0.119716] pci 0000:01:00.0: supports D1 D2
[    0.119719] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.126325] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.126332] pci 0000:00:1c.0:   bridge window [mem 0xe0400000-0xe04fffff]
[    0.126572] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11, disabled.
[    0.126640] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10, disabled.
[    0.126700] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11, disabled.
[    0.126759] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15), disabled.
[    0.126817] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.126875] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.126932] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.126990] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.127591] ACPI: \_SB_.PCI0: notify handler is installed
[    0.127652] Found 1 acpi root devices
[    0.127699] ACPI : EC: GPE = 0x24, I/O: command/status = 0x66, data = 0x62
[    0.127818] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.127824] vgaarb: loaded
[    0.127825] vgaarb: bridge control possible 0000:00:02.0
[    0.128031] SCSI subsystem initialized
[    0.128085] libata version 3.00 loaded.
[    0.128113] ACPI: bus type USB registered
[    0.128134] usbcore: registered new interface driver usbfs
[    0.128147] usbcore: registered new interface driver hub
[    0.128183] usbcore: registered new device driver usb
[    0.128301] PCI: Using ACPI for IRQ routing
[    0.129965] PCI: pci_cache_line_size set to 64 bytes
[    0.130022] e820: reserve RAM buffer [mem 0x0009e400-0x0009ffff]
[    0.130025] e820: reserve RAM buffer [mem 0x7bf7a000-0x7bffffff]
[    0.130027] e820: reserve RAM buffer [mem 0x100600000-0x103ffffff]
[    0.130123] NetLabel: Initializing
[    0.130125] NetLabel:  domain hash size = 128
[    0.130126] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.130143] NetLabel:  unlabeled traffic allowed by default
[    0.130208] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.130217] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.132261] Switched to clocksource hpet
[    0.138856] AppArmor: AppArmor Filesystem Enabled
[    0.138883] pnp: PnP ACPI init
[    0.138904] ACPI: bus type PNP registered
[    0.138972] pnp 00:00: Plug and Play ACPI device, IDs PNP0c0e (active)
[    0.139012] pnp 00:01: Plug and Play ACPI device, IDs PNP0c0e (active)
[    0.139087] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.139091] system 00:02: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.139093] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.139096] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.139099] system 00:02: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.139102] system 00:02: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.139104] system 00:02: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.139107] system 00:02: [mem 0xfed45000-0xfed8ffff] could not be reserved
[    0.139110] system 00:02: [mem 0x00f00000-0x00ffffff] has been reserved
[    0.139114] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.139320] pnp 00:03: [dma 4]
[    0.139343] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.139371] pnp 00:04: Plug and Play ACPI device, IDs INT0800 (active)
[    0.139478] system 00:05: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.139482] system 00:05: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.139520] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.139593] system 00:07: [io  0x1000-0x10fe] could not be reserved
[    0.139597] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.139626] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.139673] system 00:09: [io  0x0900-0x09fe] has been reserved
[    0.139676] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.139717] system 00:0a: [io  0x0200] has been reserved
[    0.139720] system 00:0a: [io  0x0204] has been reserved
[    0.139722] system 00:0a: [io  0x0800-0x087f] has been reserved
[    0.139725] system 00:0a: [io  0x0880-0x08ff] has been reserved
[    0.139728] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.139767] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.139804] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.139850] pnp 00:0d: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
[    0.139953] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.140082] pnp: PnP ACPI: found 15 devices
[    0.140084] ACPI: bus type PNP unregistered
[    0.146601] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.146609] pci 0000:00:1c.0:   bridge window [mem 0xe0400000-0xe04fffff]
[    0.146620] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.146623] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.146625] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.146628] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.146630] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.146632] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.146635] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.146637] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.146639] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.146642] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.146644] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.146646] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.146649] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.146651] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.146653] pci_bus 0000:00: resource 18 [mem 0x000f0000-0x000fffff]
[    0.146656] pci_bus 0000:00: resource 19 [mem 0x7ea00001-0xfebfffff]
[    0.146658] pci_bus 0000:00: resource 20 [mem 0xfed40000-0xfed44fff]
[    0.146661] pci_bus 0000:01: resource 1 [mem 0xe0400000-0xe04fffff]
[    0.146697] NET: Registered protocol family 2
[    0.146882] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.146939] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.146987] TCP: Hash tables configured (established 16384 bind 16384)
[    0.147010] TCP: reno registered
[    0.147018] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.147033] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.147091] NET: Registered protocol family 1
[    0.147105] pci 0000:00:02.0: Boot video device
[    0.147609] PCI: CLS 64 bytes, default 64
[    0.147680] Trying to unpack rootfs image as initramfs...
[    0.607895] Freeing initrd memory: 18592K (ffff880035ba0000 - ffff880036dc8000)
[    0.607900] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.607904] software IO TLB [mem 0x75800000-0x79800000] (64MB) mapped at [ffff880075800000-ffff8800797fffff]
[    0.608075] microcode: CPU0 sig=0x40651, pf=0x40, revision=0x15
[    0.608084] microcode: CPU1 sig=0x40651, pf=0x40, revision=0x15
[    0.608137] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.608140] Scanning for low memory corruption every 60 seconds
[    0.608438] Initialise system trusted keyring
[    0.608495] audit: initializing netlink socket (disabled)
[    0.608506] type=2000 audit(1397860595.604:1): initialized
[    0.649637] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.651114] VFS: Disk quotas dquot_6.5.2
[    0.651163] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.651670] fuse init (API version 7.22)
[    0.651762] msgmni has been set to 3746
[    0.651829] Key type big_key registered
[    0.652229] Key type asymmetric registered
[    0.652232] Asymmetric key parser 'x509' registered
[    0.652267] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.652300] io scheduler noop registered
[    0.652302] io scheduler deadline registered (default)
[    0.652329] io scheduler cfq registered
[    0.652571] pcieport 0000:00:1c.0: irq 56 for MSI/MSI-X
[    0.652682] aer 0000:00:1c.0:pcie02: service driver aer loaded
[    0.652698] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.652700] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.652705] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.652719] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.652736] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.652782] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    0.652783] vesafb: scrolling: redraw
[    0.652786] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.653346] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90004400000, using 4160k, total 4160k
[    0.657450] Console: switching to colour frame buffer device 170x48
[    0.661416] fb0: VESA VGA frame buffer device
[    0.661445] intel_idle: MWAIT substates: 0x11142120
[    0.661447] intel_idle: v0.4 model 0x45
[    0.661449] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.661548] ipmi message handler version 39.2
[    0.661643] ACPI: AC Adapter [AC] (on-line)
[    0.661726] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.661755] ACPI: Lid Switch [LID0]
[    0.661795] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.661800] ACPI: Power Button [PWRB]
[    0.661833] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.661837] ACPI: Sleep Button [TPAD]
[    0.661870] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:01/input/input3
[    0.661873] ACPI: Sleep Button [TSCR]
[    0.661923] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[    0.661926] ACPI: Power Button [PWRF]
[    0.661988] ACPI: Fan [TDP0] (off)
[    0.662021] ACPI: Fan [TDP1] (on)
[    0.662828] thermal LNXTHERM:00: registered as thermal_zone0
[    0.662832] ACPI: Thermal Zone [THRM] (36 C)
[    0.662861] GHES: HEST is not enabled!
[    0.662955] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.663380] ACPI: Battery Slot [BAT0] (battery present)
[    0.664379] Linux agpgart interface v0.103
[    0.664499] tpm_tis 00:0d: 1.2 TPM (device-id 0xB, rev-id 16)
[    0.935095] brd: module loaded
[    0.936105] loop: module loaded
[    0.936528] libphy: Fixed MDIO Bus: probed
[    0.936627] tun: Universal TUN/TAP device driver, 1.6
[    0.936629] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.936678] PPP generic driver version 2.4.2
[    0.936723] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.936727] ehci-pci: EHCI PCI platform driver
[    0.936912] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.936919] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    0.936934] ehci-pci 0000:00:1d.0: debug port 2
[    0.940824] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.940851] ehci-pci 0000:00:1d.0: irq 19, io mem 0xe051f800
[    0.952138] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.952188] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.952190] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.952193] usb usb1: Product: EHCI Host Controller
[    0.952195] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    0.952197] usb usb1: SerialNumber: 0000:00:1d.0
[    0.952350] hub 1-0:1.0: USB hub found
[    0.952359] hub 1-0:1.0: 2 ports detected
[    0.952476] ehci-platform: EHCI generic platform driver
[    0.952487] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.952489] ohci-pci: OHCI PCI platform driver
[    0.952499] ohci-platform: OHCI generic platform driver
[    0.952506] uhci_hcd: USB Universal Host Controller Interface driver
[    0.952671] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.952677] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.952768] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.952791] xhci_hcd 0000:00:14.0: irq 57 for MSI/MSI-X
[    0.952865] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.952867] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.952870] usb usb2: Product: xHCI Host Controller
[    0.952872] usb usb2: Manufacturer: Linux 3.13.0-24-generic xhci_hcd
[    0.952874] usb usb2: SerialNumber: 0000:00:14.0
[    0.953006] hub 2-0:1.0: USB hub found
[    0.953019] hub 2-0:1.0: 8 ports detected
[    0.953294] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.953300] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.953348] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003
[    0.953350] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.953352] usb usb3: Product: xHCI Host Controller
[    0.953355] usb usb3: Manufacturer: Linux 3.13.0-24-generic xhci_hcd
[    0.953357] usb usb3: SerialNumber: 0000:00:14.0
[    0.953481] hub 3-0:1.0: USB hub found
[    0.953491] hub 3-0:1.0: 4 ports detected
[    0.960295] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.960298] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.960835] i8042: Warning: Keylock active
[    0.960974] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.961305] mousedev: PS/2 mouse device common for all mice
[    0.961991] rtc_cmos 00:08: RTC can wake from S4
[    0.962190] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.962237] rtc_cmos 00:08: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.962336] device-mapper: uevent: version 1.0.3
[    0.962427] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.962434] ledtrig-cpu: registered to indicate activity on CPUs
[    0.962564] TCP: cubic registered
[    0.962686] NET: Registered protocol family 10
[    0.962907] NET: Registered protocol family 17
[    0.962917] Key type dns_resolver registered
[    0.963231] Loading compiled-in X.509 certificates
[    0.964502] Loaded X.509 cert 'Magrathea: Glacier signing key: 00a5a65759de474bc5c43120880c1b94a539f431'
[    0.964515] registered taskstats version 1
[    0.964896] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.967605] Key type trusted registered
[    0.970209] Key type encrypted registered
[    0.972853] AppArmor: AppArmor sha1 policy hashing enabled
[    1.264188] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.396509] usb 1-1: New USB device found, idVendor=8087, idProduct=8000
[    1.396515] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.396757] hub 1-1:1.0: USB hub found
[    1.396863] hub 1-1:1.0: 8 ports detected
[    1.564143] usb 2-3: new high-speed USB device number 2 using xhci_hcd
[    1.604088] tsc: Refined TSC clocksource calibration: 1396.767 MHz
[    1.650747] usb 2-3: New USB device found, idVendor=1bcf, idProduct=2c67
[    1.650753] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.650756] usb 2-3: Product: HD WebCam
[    1.650758] usb 2-3: Manufacturer: NC.21411.02434809E19LM0001
[    1.832088] usb 2-4: new full-speed USB device number 3 using xhci_hcd
[    1.849632] usb 2-4: string descriptor 0 malformed (err = -61), defaulting to 0x0409
[    1.851604] usb 2-4: New USB device found, idVendor=0489, idProduct=e056
[    1.851607] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.604071] Switched to clocksource tsc
[   53.791731] regulator-dummy: disabling
[   53.791791]   Magic number: 10:256:654
[   53.791901] rtc_cmos 00:08: setting system clock to 2014-04-18 22:37:29 UTC (1397860649)
[   53.792272] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   53.792276] EDD information not available.
[   53.792315] PM: Hibernation image not present or could not be loaded.
[   53.793489] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
[   53.793491] Write protecting the kernel read-only data: 12288k
[   53.796748] Freeing unused kernel memory: 844K (ffff88000172d000 - ffff880001800000)
[   53.799211] Freeing unused kernel memory: 708K (ffff880001b4f000 - ffff880001c00000)
[   53.818144] systemd-udevd[100]: starting version 204
[   53.850004] ahci 0000:00:1f.2: version 3.0
[   53.850190] ahci 0000:00:1f.2: irq 58 for MSI/MSI-X
[   53.850215] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[   53.850233] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x1 impl SATA mode
[   53.850237] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo only pio slum part deso sadm sds apst 
[   53.850487] scsi0 : ahci
[   53.850563] scsi1 : ahci
[   53.850603] ata1: SATA max UDMA/133 abar m2048@0xe051f000 port 0xe051f100 irq 58
[   53.850605] ata2: DUMMY
[   54.167377] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[   54.167580] ata1.00: ATA-10: KINGSTON SNS4151S316G, S9FM01.1, max UDMA/100
[   54.167585] ata1.00: 31277232 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[   54.167965] ata1.00: configured for UDMA/100
[   54.168252] scsi 0:0:0:0: Direct-Access     ATA      KINGSTON SNS4151 S9FM PQ: 0 ANSI: 5
[   54.168472] sd 0:0:0:0: [sda] 31277232 512-byte logical blocks: (16.0 GB/14.9 GiB)
[   54.168479] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   54.168534] sd 0:0:0:0: [sda] Write Protect is off
[   54.168538] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   54.168561] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.169097]  sda: sda1 sda2 < sda5 >
[   54.169832] sd 0:0:0:0: [sda] Attached SCSI disk
[   54.206862] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   54.301319] random: init urandom read with 34 bits of entropy available
[   54.338124] init: plymouth-upstart-bridge main process (153) terminated with status 1
[   54.338141] init: plymouth-upstart-bridge main process ended, respawning
[   54.349491] init: plymouth-upstart-bridge main process (163) terminated with status 1
[   54.349510] init: plymouth-upstart-bridge main process ended, respawning
[   54.357270] init: plymouth-upstart-bridge main process (166) terminated with status 1
[   54.357286] init: plymouth-upstart-bridge main process ended, respawning
[   54.587352] Adding 2034684k swap on /dev/sda5.  Priority:-1 extents:1 across:2034684k SSFS
[   54.773967] systemd-udevd[278]: starting version 204
[   54.892336] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   54.896135] lp: driver loaded but no devices found
[   54.933170] ppdev: user-space parallel port driver
[   54.937300] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   54.943385] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   54.988657] [drm] Initialized drm 1.1.0 20060810
[   55.049323] Bluetooth: Core ver 2.17
[   55.049638] NET: Registered protocol family 31
[   55.049642] Bluetooth: HCI device and connection manager initialized
[   55.049653] Bluetooth: HCI socket layer initialized
[   55.049657] Bluetooth: L2CAP socket layer initialized
[   55.049664] Bluetooth: SCO socket layer initialized
[   55.056926] usbcore: registered new interface driver btusb
[   55.060177] i2c_designware_core: module verification failed: signature and/or  required key missing - tainting kernel
[   55.093158] cfg80211: Calling CRDA to update world regulatory domain
[   55.206790] usb 2-4: USB disconnect, device number 3
[   55.226965] [drm] Memory usable by graphics device = 2048M
[   55.226971] checking generic (d0000000 410000) vs hw (d0000000 10000000)
[   55.226973] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   55.226995] Console: switching to colour dummy device 80x25
[   55.340420] usbcore: registered new interface driver ath3k
[   55.341199] i915 0000:00:02.0: irq 59 for MSI/MSI-X
[   55.341212] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   55.341213] [drm] Driver supports precise vblank timestamp query.
[   55.341313] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   55.420981] Linux video capture interface: v2.00
[   55.439179] random: nonblocking pool is initialized
[   55.459660] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   55.459664] Bluetooth: BNEP filters: protocol multicast
[   55.459675] Bluetooth: BNEP socket layer initialized
[   55.488706] ath: phy0: ASPM enabled: 0x43
[   55.488711] ath: EEPROM regdomain: 0x6c
[   55.488713] ath: EEPROM indicates we should expect a direct regpair map
[   55.488716] ath: Country alpha2 being used: 00
[   55.488717] ath: Regpair used: 0x6c
[   55.504090] Bluetooth: RFCOMM TTY layer initialized
[   55.504104] Bluetooth: RFCOMM socket layer initialized
[   55.504112] Bluetooth: RFCOMM ver 1.11
[   55.528624] uvcvideo: Found UVC 1.00 device HD WebCam (1bcf:2c67)
[   55.556391] input: HD WebCam as /devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.0/input/input7
[   55.558387] usbcore: registered new interface driver uvcvideo
[   55.558391] USB Video Class driver (1.1.1)
[   55.575112] usb 2-4: new full-speed USB device number 4 using xhci_hcd
[   55.588570] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   55.588911] type=1400 audit(1397860651.292:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=492 comm="apparmor_parser"
[   55.588920] type=1400 audit(1397860651.292:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=492 comm="apparmor_parser"
[   55.589020] ieee80211 phy0: Atheros AR9462 Rev:2 mem=0xffffc90004500000, irq=16
[   55.594284] type=1400 audit(1397860651.296:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=492 comm="apparmor_parser"
[   55.594688] usb 2-4: string descriptor 0 malformed (err = -61), defaulting to 0x0409
[   55.596783] usb 2-4: New USB device found, idVendor=0489, idProduct=e056
[   55.596788] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   55.759353] type=1400 audit(1397860651.464:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=530 comm="apparmor_parser"
[   55.759363] type=1400 audit(1397860651.464:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=530 comm="apparmor_parser"
[   55.759368] type=1400 audit(1397860651.464:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=530 comm="apparmor_parser"
[   55.760207] type=1400 audit(1397860651.464:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=530 comm="apparmor_parser"
[   55.760215] type=1400 audit(1397860651.464:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=530 comm="apparmor_parser"
[   55.761189] type=1400 audit(1397860651.464:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=530 comm="apparmor_parser"
[   55.787612] fbcon: inteldrmfb (fb0) is primary device
[   55.934500] cfg80211: World regulatory domain updated:
[   55.934501] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   55.934504] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   55.934505] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   55.934506] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   55.934507] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   55.934508] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   55.967310] isl29018: module is from the staging directory, the quality is unknown, you have been warned.
[   55.970181] isl29018 1-0044: No cache defaults, reading back from HW
[   56.067485] input: Cypress APA Trackpad (cyapa) as /devices/pci0000:00/0000:00:15.1/i2c-0/0-0067/input/input8
[   56.810995] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   57.402879] Console: switching to colour frame buffer device 170x48
[   57.407155] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   57.407156] i915 0000:00:02.0: registered panic notifier
[   57.430569] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   57.431108] snd_hda_intel 0000:00:1b.0: irq 60 for MSI/MSI-X
[   57.498397] i915_bdw: exports duplicate symbol i915_release_power_well (owned by i915)
[   57.511152] HDA driver get symbol successfully from i915 module
[   57.517608] SKU: Nid=0x0 sku_cfg=0x00000283
[   57.517612] SKU: port_connectivity=0x0
[   57.517613] SKU: enable_pcbeep=0x1
[   57.517615] SKU: check_sum=0x00000000
[   57.517617] SKU: customization=0x00000000
[   57.517618] SKU: external_amp=0x0
[   57.517619] SKU: platform_type=0x0
[   57.517621] SKU: swap=0x1
[   57.517622] SKU: override=0x1
[   57.517842] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   57.517844]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   57.517846]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   57.517847]    mono: mono_out=0x0
[   57.517848]    inputs:
[   57.517851]      Internal Mic=0x1a
[   57.517852]      Mic=0x19
[   57.517854] realtek: Enabling init ASM_ID=0x0283 CODEC_ID=10ec0283
[   57.522802] snd_hda_intel 0000:00:03.0: irq 61 for MSI/MSI-X
[   57.553431] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
[   57.553743] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input9
[   57.589211] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input13
[   57.589308] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input12
[   57.589370] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input11
[   57.669397] init: failsafe main process (583) killed by TERM signal
[   57.673100] init: samba-ad-dc main process (631) terminated with status 1
[   57.853084] init: udev-fallback-graphics main process (690) terminated with status 1
[   58.079232] type=1400 audit(1397860653.784:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=750 comm="apparmor_parser"
[   58.121468] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.126143] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.870441] hidraw: raw HID events driver (C) Jiri Kosina
[   58.874883] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   58.874897] Bluetooth: HIDP socket layer initialized
[   58.879533] hid-generic 0005:046D:B007.0001: unknown main item tag 0x0
[   58.882375] input: Logitech MX Revolution Mouse as /devices/pci0000:00/0000:00:14.0/usb2/2-4/2-4:1.0/bluetooth/hci0/hci0:21/input14
[   58.886666] hid-generic 0005:046D:B007.0001: input,hidraw0: BLUETOOTH HID v0.19 Mouse [Logitech MX Revolution Mouse] on 48:5a:b6:61:9b:78
[   59.991790] init: plymouth-upstart-bridge main process ended, respawning
[   65.074083] wlan0: authenticate with 4c:5e:0c:2c:b0:81
[   65.091711] wlan0: send auth to 4c:5e:0c:2c:b0:81 (try 1/3)
[   65.095982] wlan0: authenticated
[   65.105588] wlan0: associate with 4c:5e:0c:2c:b0:81 (try 1/3)
[   65.121102] wlan0: RX AssocResp from 4c:5e:0c:2c:b0:81 (capab=0x431 status=0 aid=4)
[   65.121151] wlan0: associated
[   65.121179] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   65.300550] wlan0: deauthenticating from 4c:5e:0c:2c:b0:81 by local choice (reason=2)
[   65.308432] cfg80211: Calling CRDA to update world regulatory domain
[   65.308622] wlan0: authenticate with 4c:5e:0c:2c:b0:81
[   65.333532] wlan0: send auth to 4c:5e:0c:2c:b0:81 (try 1/3)
[   65.333738] cfg80211: World regulatory domain updated:
[   65.333743] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   65.333746] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.333748] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.333750] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   65.333752] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.333754] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.356079] wlan0: authenticated
[   65.357478] wlan0: associate with 4c:5e:0c:2c:b0:81 (try 1/3)
[   65.386501] wlan0: RX AssocResp from 4c:5e:0c:2c:b0:81 (capab=0x431 status=0 aid=4)
[   65.386551] wlan0: associated





edit: this is after a fresh install of 14.04 xubuntu...

---

### Post by Professor Frink on 2014-04-22
I have the same init: plymouth-upstart-bridge main process ended, respawning bug as well on a haswell pentium G3220.  Do you think it's a haswell bug that's causing the slow boot time?

Ubuntu Server 14.04

---

### Post by layuser1 on 2014-04-25
using chrubuntu and touchpad works fine on my c720

---

### Post by vandend278 on 2015-03-29
I'm yet to see a Ubuntu plymouth boot screen on a Chromebook install

---

