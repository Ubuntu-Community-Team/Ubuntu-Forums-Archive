---
title: "Lubuntu 16.04.03 Boot Failure with 4.13"
date: 2018-01-15
forum: Installation &amp; Upgrades
---

### Post by Suudy on 2018-01-15
[COLOR=#111111][FONT=Ubuntu]I updated the kernel HW on Lubuntu 16.04.03 recently, which install 4.13.0-26. Now upon reboot, it shows the "Loading initial ramdisk ...." then immediately reboots.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've removed quiet and splash, and tried adding nomodeset, debug, andearlyprintk=vga(separately and together). Unlike several of the other cases I've found online, mine does not freeze at this point, but does a restart. I can boot successfully with 4.10.0-42.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
I also tried a reinstall of the kernel with sudo apt install --reinstall linux-image-generic-hwe-16.04, and no change.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
I'm unsure how to get more information to determine the root cause of the boot failure. I'm running a vanilla install with no special drivers on a Dell Optiplex 960. No EFI, but BIOS boot.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Any tips on debug or what the issue might be?[/FONT][/COLOR]

---

### Post by Suudy on 2018-01-16
[COLOR=#111111][FONT=Ubuntu]Ok, I've tried a couple of things. First, I can get some output on the console by changing [/FONT][/COLOR]earlyprintk[COLOR=#111111][FONT=Ubuntu] to [/FONT][/COLOR]earlyprintk=vga,keep[COLOR=#111111][FONT=Ubuntu]. However, it reboots very quickly. I tried a serial console ([/FONT][/COLOR]console=ttyS0,115200[COLOR=#111111][FONT=Ubuntu]) and connecting a null modem, but nothing comes out on the other end.[/FONT][/COLOR]

---

### Post by Suudy on 2018-01-17
Ok, I managed to get some serial console output with earlyprintk=serial:

```
[    0.000000] random: get_random_bytes called from start_kernel+0x35/0x41c with crng_init=0
[    0.000000] Linux version 4.13.0-26-generic (buildd@lgw01-amd64-036) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.5)) #29~16.04.2-Ubuntu SMP Tue Jan 9 21:38:24 UTC 2018 (Ubuntu 4.13.0-26.29~16.04.2-generic 4.13.13)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
[    0.000000] x86/fpu: Enabled xstate features 0x3, context size is 576 bytes, using 'standard' format.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ebff] usable
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bd9ffbff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bd9ffc00-0x00000000bda53bff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bda53c00-0x00000000bda55bff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bda55c00-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed20000-0x00000000fed9ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000feefffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000177ffffff] usable
[    0.000000] console [earlyser0] enabled
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] random: fast init done
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: Dell Inc. OptiPlex 960                 /0Y958C, BIOS A03 02/17/2009
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] e820: last_pfn = 0x178000 max_arch_pfn = 0x1000000
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] found SMP MP-table at [mem 0x000fe710-0x000fe71f] mapped at [c00fe710]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] RAMDISK: [mem 0x32512000-0x35280fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000FEC00 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 0x00000000000FC7CD 00008C (v01 DELL   B10K     00000015 ASL  00000061)
[    0.000000] ACPI: FACP 0x00000000000FC8FD 0000F4 (v03 DELL   B10K     00000015 ASL  00000061)
[    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe0Block: 128/64 (20170531/tbfadt-603)
[    0.000000] ACPI: DSDT 0x00000000FFE9CFCA 00545E (v01 DELL   dt_ex    00001000 INTL 20050624)
[    0.000000] ACPI: FACS 0x00000000BD9FFC00 000040
[    0.000000] ACPI: FACS 0x00000000BD9FFC00 000040
[    0.000000] ACPI: SSDT 0x00000000FFEA2547 0000AA (v01 DELL   st_ex    00001000 INTL 20050624)
[    0.000000] ACPI: APIC 0x00000000000FC9F1 000092 (v01 DELL   B10K     00000015 ASL  00000061)
[    0.000000] ACPI: BOOT 0x00000000000FCA83 000028 (v01 DELL   B10K     00000015 ASL  00000061)
[    0.000000] ACPI: ASF! 0x00000000000FCAAB 000096 (v32 DELL   B10K     00000015 ASL  00000061)
[    0.000000] ACPI: MCFG 0x00000000000FCB41 00003E (v01 DELL   B10K     00000015 ASL  00000061)
[    0.000000] ACPI: HPET 0x00000000000FCB7F 000038 (v01 DELL   B10K     00000015 ASL  00000061)
[    0.000000] ACPI: TCPA 0x00000000000FCDDB 000032 (v01 DELL   B10K     00000015 ASL  00000061)
[    0.000000] ACPI: DMAR 0x00000000000FCE0D 000120 (v01 DELL   B10K     00000015 ASL  00000061)
[    0.000000] ACPI: SLIC 0x00000000000FCBB7 000176 (v01 DELL   B10K     00000015 ASL  00000061)
[    0.000000] ACPI: SSDT 0x00000000BD9FFC40 0001F9 (v01 DpgPmm Cpu0Ist  00000011 INTL 20050624)
[    0.000000] ACPI: SSDT 0x00000000BDA00049 0001F9 (v01 DpgPmm Cpu1Ist  00000011 INTL 20050624)
[    0.000000] ACPI: SSDT 0x00000000BDA00452 000190 (v01 DpgPmm CpuPm    00000010 INTL 20050624)
[    0.000000] 5126MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   Normal   [mem 0x0000000001000000-0x00000000379fdfff]
[    0.000000]   HighMem  [mem 0x00000000379fe000-0x0000000177ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009dfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000bd9fefff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x0000000177ffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x0000000177ffffff]
[    0.000000] Using APIC driver default
[    0.000000] Reserving Intel graphics memory at 0x00000000be000000-0x00000000bfffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] percpu: Embedded 31 pages/cpu @f5603000 s94284 r0 d32692 u126976
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1265899
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-26-generic root=UUID=f74edde2-ad94-4ea1-b340-f9c8e9c728e5 ro debug loglevel=7 earlyprintk=serial,ttyS0,115200,keep intel_iommu=off panic=30 console=ttyS0,115200
[    0.000000] DMAR: IOMMU disabled
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] microcode: microcode updated early to revision 0xa0b, date = 2010-09-28
[    0.000000] Initializing CPU#0
[    0.000000] Initializing HighMem for node 0 (000379fe:00178000)
[    0.000000] Initializing Movable for node 0 (00000000:00000000)
[    0.000000] Memory: 4957884K/5072496K available (8497K kernel code, 876K rwdata, 3332K rodata, 1092K init, 852K bss, 114612K reserved, 0K cma-reserved, 4161540K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]   cpu_entry : 0xffc00000 - 0xffd39000   (1252 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc6c7e000 - 0xc6d8f000   (1092 kB)
[    0.000000]       .data : 0xc684c7c6 - 0xc6c6b2c0   (4218 kB)
[    0.000000]       .text : 0xc6000000 - 0xc684c7c6   (8497 kB)
```

---

### Post by warp07 on 2018-01-18
I also ... :( Ubuntu16.04.3, the new kernel (4.13.0-26) did the same thing. I went back to 4.10.0-42, the system works, but strange stuff ...
1) the rendering of the texts in the main menu submenu was broken (black)
[IMG]https://i.imgur.com/VNKlTkq.png[/IMG] [IMG]https://i.imgur.com/sBIVQho.png[/IMG]
[IMG]https://i.imgur.com/6FdYPcj.png[/IMG] [IMG]https://i.imgur.com/1RGXOlM.png[/IMG]

2) review Synaptic for xserver-xorg-hwe-16.04 yes until linux-generic-hwe-16.04 is installed. Is this not a problem?

---

### Post by Suudy on 2018-01-18
As a followup, I found [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742675](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742675) which shows adding acpi=off to the command line fixes it.  And it does for my system as well.

---

