---
title: "Upgrade to 10.04 broke ALL sound input"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by destiney on 2010-05-09
I upgraded my system to Ubuntu 10.04 this morning.  I've spent the last 6 hours or so pulling my hair out trying to figure out why my sound input no longer works.  My tv card (WinTV, bt878 ) can no longer be heard.  It worked fine before the upgrade this morning.  This seems to be just a symptom of a larger problem.

I have two microphone jacks and one line-in jack on my onboard sound.  None of them will accept any sort of sound input now.  I have my tv card running into my line-in jack, I can no longer hear my tv application.  I see it just fine.  I use tvtime.  My tv app is not the problem, I have plugged my HTC Hero into all the mic and line-in jacks as well, and nothing can be heard when I play an mp3.

This system is dual boot with Win7.  All of the jacks work fine in Win7.

I went into my junk closet and dug out an old Sound Blaster card and put it in.  It's recognized under Linux as an ES1371.  Alsa recognizes it just fine.  It has one mic input and one line-in jack.  Neither of those will accept sound input either.  Sound output works fine, just like with my onboard sound.

I have made sure nothing is muted using alsamixer.

Here is the output from amixer:

```

Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 23 [74%] [-12.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 253 [99%] [0.40dB]
  Front Right: Playback 253 [99%] [0.40dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 17 [55%] [-21.00dB] [on]
  Front Right: Playback 17 [55%] [-21.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 10 [32%] [-19.50dB] [off]
  Front Right: Playback 10 [32%] [-19.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 1 [33%]
  Front Right: 1 [33%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 19 [61%] [-18.00dB] [on]
  Front Right: Playback 19 [61%] [-18.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 16 [52%] [-22.50dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 12 [39%] [-16.50dB] [off]
  Front Right: Playback 12 [39%] [-16.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%]
  Front Right: 3 [100%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 27 [87%] [24.00dB] [on]
  Front Right: Capture 27 [87%] [24.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 13 [42%] [3.00dB] [on]
  Front Right: Capture 13 [42%] [3.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'

```

Here is the output from lspci:

```

> lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 12)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 12)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 12)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 12)
00:10.0 PIC: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 12)
00:10.1 PIC: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 12)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 12)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 12)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 12)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 12)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
02:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1)
04:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
04:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
05:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
08:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
08:01.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)

```

Here is the dmesg output:

```

> dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=b8e3f4e6-588a-4dea-80a3-6c412a039742 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4c00 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf680000 (usable)
[    0.000000]  BIOS-e820: 00000000bf680000 - 00000000bf698000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf698000 - 00000000bf6dc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6dc000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000340000000 (usable)
[    0.000000] DMI 2.5 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x340000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E3FFF write-protect
[    0.000000]   E4000-EBFFF write-through
[    0.000000]   EC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask F00000000 write-back
[    0.000000]   2 base 300000000 mask FC0000000 write-back
[    0.000000]   3 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   4 base 0BF700000 mask FFFF00000 uncachable
[    0.000000]   5 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bf700000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbf680 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4c00 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf680000 (usable)
[    0.000000]  modified: 00000000bf680000 - 00000000bf698000 (ACPI data)
[    0.000000]  modified: 00000000bf698000 - 00000000bf6dc000 (ACPI NVS)
[    0.000000]  modified: 00000000bf6dc000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000340000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf680000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf680000 page 4k
[    0.000000] kernel direct mapping tables up to bf680000 @ 10000-15000
[    0.000000] init_memory_mapping: 0000000100000000-0000000340000000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0100000000 - 0340000000 page 2M
[    0.000000] kernel direct mapping tables up to 340000000 @ 13000-21000
[    0.000000] RAMDISK: 3788e000 - 37feff8c
[    0.000000] ACPI: RSDP 00000000000fabd0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bf680000 00040 (v01 022609 RSDT1156 20090226 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bf680200 00084 (v01 022609 FACP1156 20090226 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bf6804b0 0C3DD (v01  A1146 A1146001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000bf698000 00040
[    0.000000] ACPI: APIC 00000000bf680390 000D8 (v01 022609 APIC1156 20090226 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bf680470 0003C (v01 022609 OEMMCFG  20090226 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bf698040 00072 (v01 022609 OEMB1156 20090226 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bf68f4b0 00038 (v01 022609 OEMHPET  20090226 MSFT 00000097)
[    0.000000] ACPI: OSFR 00000000bf68f4f0 000B0 (v01 022609 OEMOSFR  20090226 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bf69a140 0249F (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000340000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000340000000
[    0.000000]   NODE_DATA [000000000001c000 - 0000000000020fff]
[    0.000000]   bootmap [0000000000021000 -  0000000000088fff] pages 68
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0340000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [003788e000 - 0037feff8c]          RAMDISK ==> [003788e000 - 0037feff8c]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e3288]              BRK ==> [00019e3000 - 00019e3288]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #7 [0000013000 - 000001c000]          PGTABLE ==> [0000013000 - 000001c000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea000b5fffff] PMD -> [ffff880028600000-ffff880032dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00340000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf680
[    0.000000]     0: 0x00100000 -> 0x00340000
[    0.000000] On node 0 totalpages: 3143183
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 111 pages reserved
[    0.000000]   DMA zone: 3816 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 765624 pages, LIFO batch:31
[    0.000000]   Normal zone: 32256 pages used for memmap
[    0.000000]   Normal zone: 2327040 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec8a000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 9, version 32, address 0xfec8a000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 16 CPUs, 8 hotplug CPUs
[    0.000000] nr_irqs_gsi: 48
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e5000
[    0.000000] PM: Registered nosave memory: 00000000000e5000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf680000 - 00000000bf698000
[    0.000000] PM: Registered nosave memory: 00000000bf698000 - 00000000bf6dc000
[    0.000000] PM: Registered nosave memory: 00000000bf6dc000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028034000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 3096480
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=b8e3f4e6-588a-4dea-80a3-6c412a039742 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 12314792k/13631488k available (5313k kernel code, 1058756k absent, 257940k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:944
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2672.535 MHz processor.
[    0.001792] Console: colour VGA+ 80x25
[    0.001793] console [tty0] enabled
[    0.021985] allocated 125829120 bytes of page_cgroup
[    0.021987] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.022103] hpet clockevent registered
[    0.022105] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.022110] Calibrating delay loop (skipped), value calculated using timer frequency.. 5345.07 BogoMIPS (lpj=26725350)
[    0.022125] Security Framework initialized
[    0.022137] AppArmor: AppArmor initialized
[    0.023032] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.025947] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.027179] Mount-cache hash table entries: 256
[    0.027267] Initializing cgroup subsys ns
[    0.027270] Initializing cgroup subsys cpuacct
[    0.027273] Initializing cgroup subsys memory
[    0.027277] Initializing cgroup subsys freezer
[    0.027278] Initializing cgroup subsys net_cls
[    0.027287] CPU: Physical Processor ID: 0
[    0.027288] CPU: Processor Core ID: 0
[    0.027291] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.027292] CPU: L2 cache: 256K
[    0.027293] CPU: L3 cache: 8192K
[    0.027295] CPU 0/0x0 -> Node 0
[    0.027297] mce: CPU supports 9 MCE banks
[    0.027306] CPU0: Thermal monitoring enabled (TM1)
[    0.027309] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6 CMCI:8
[    0.027315] using mwait in idle threads.
[    0.027316] Performance Counters: Nehalem/Corei7 events, Intel PMU driver.
[    0.027320] ... version:                 3
[    0.027321] ... bit width:               48
[    0.027322] ... generic counters:        4
[    0.027323] ... value mask:              0000ffffffffffff
[    0.027324] ... max period:              000000007fffffff
[    0.027325] ... fixed-purpose counters:  3
[    0.027326] ... counter mask:            000000070000000f
[    0.028924] ACPI: Core revision 20090521
[    0.065534] Setting APIC routing to flat
[    0.065978] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.165945] CPU0: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    0.282136] Booting processor 1 APIC 0x2 ip 0x6000
[    0.292396] Initializing CPU#1
[    0.441972] Calibrating delay using timer specific routine.. 5345.50 BogoMIPS (lpj=26727543)
[    0.441978] CPU: Physical Processor ID: 0
[    0.441979] CPU: Processor Core ID: 1
[    0.441981] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.441982] CPU: L2 cache: 256K
[    0.441983] CPU: L3 cache: 8192K
[    0.441985] CPU 1/0x2 -> Node 0
[    0.441987] mce: CPU supports 9 MCE banks
[    0.441995] CPU1: Thermal monitoring enabled (TM1)
[    0.441997] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.442642] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.443244] CPU1: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    0.443251] Skipping synchronization checks as TSC is reliable.
[    0.443317] Booting processor 2 APIC 0x4 ip 0x6000
[    0.453573] Initializing CPU#2
[    0.601920] Calibrating delay using timer specific routine.. 5345.39 BogoMIPS (lpj=26726978)
[    0.601928] CPU: Physical Processor ID: 0
[    0.601929] CPU: Processor Core ID: 2
[    0.601931] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.601932] CPU: L2 cache: 256K
[    0.601933] CPU: L3 cache: 8192K
[    0.601935] CPU 2/0x4 -> Node 0
[    0.601937] mce: CPU supports 9 MCE banks
[    0.601945] CPU2: Thermal monitoring enabled (TM1)
[    0.601948] CPU 2 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.602591] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
[    0.603174] CPU2: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    0.603181] Skipping synchronization checks as TSC is reliable.
[    0.603251] Booting processor 3 APIC 0x6 ip 0x6000
[    0.613608] Initializing CPU#3
[    0.761865] Calibrating delay using timer specific routine.. 5345.50 BogoMIPS (lpj=26727542)
[    0.761871] CPU: Physical Processor ID: 0
[    0.761872] CPU: Processor Core ID: 3
[    0.761874] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.761876] CPU: L2 cache: 256K
[    0.761876] CPU: L3 cache: 8192K
[    0.761878] CPU 3/0x6 -> Node 0
[    0.761880] mce: CPU supports 9 MCE banks
[    0.761888] CPU3: Thermal monitoring enabled (TM1)
[    0.761891] CPU 3 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
[    0.762534] x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106
[    0.763158] CPU3: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    0.763165] Skipping synchronization checks as TSC is reliable.
[    0.763234] Booting processor 4 APIC 0x1 ip 0x6000
[    0.773591] Initializing CPU#4
[    0.921813] Calibrating delay using timer specific routine.. 5345.39 BogoMIPS (lpj=26726960)
[    0.921822] CPU: Physical Processor ID: 0
[    0.921823] CPU: Processor Core ID: 0
[    0.921825] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.921827] CPU: L2 cache: 256K
[    0.921828] CPU: L3 cache: 8192K
[    0.921830] CPU 4/0x1 -> Node 0
[    0.921833] mce: CPU supports 9 MCE banks
[    0.921842] CPU4: Thermal monitoring enabled (TM1)
[    0.921845] CPU 4 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
[    0.922636] x86 PAT enabled: cpu 4, old 0x7040600070406, new 0x7010600070106
[    0.923467] CPU4: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    0.923474] Skipping synchronization checks as TSC is reliable.
[    0.923548] Booting processor 5 APIC 0x3 ip 0x6000
[    0.933804] Initializing CPU#5
[    1.081760] Calibrating delay using timer specific routine.. 5192.92 BogoMIPS (lpj=25964604)
[    1.081767] CPU: Physical Processor ID: 0
[    1.081768] CPU: Processor Core ID: 1
[    1.081770] CPU: L1 I cache: 32K, L1 D cache: 32K
[    1.081771] CPU: L2 cache: 256K
[    1.081772] CPU: L3 cache: 8192K
[    1.081774] CPU 5/0x3 -> Node 0
[    1.081776] mce: CPU supports 9 MCE banks
[    1.081784] CPU5: Thermal monitoring enabled (TM1)
[    1.081786] CPU 5 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
[    1.082605] x86 PAT enabled: cpu 5, old 0x7040600070406, new 0x7010600070106
[    1.083507] CPU5: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    1.083515] Skipping synchronization checks as TSC is reliable.
[    1.083582] Booting processor 6 APIC 0x5 ip 0x6000
[    1.093838] Initializing CPU#6
[    1.241705] Calibrating delay using timer specific routine.. 5345.50 BogoMIPS (lpj=26727540)
[    1.241711] CPU: Physical Processor ID: 0
[    1.241712] CPU: Processor Core ID: 2
[    1.241714] CPU: L1 I cache: 32K, L1 D cache: 32K
[    1.241715] CPU: L2 cache: 256K
[    1.241716] CPU: L3 cache: 8192K
[    1.241717] CPU 6/0x5 -> Node 0
[    1.241719] mce: CPU supports 9 MCE banks
[    1.241727] CPU6: Thermal monitoring enabled (TM1)
[    1.241729] CPU 6 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
[    1.242547] x86 PAT enabled: cpu 6, old 0x7040600070406, new 0x7010600070106
[    1.243389] CPU6: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    1.243396] Skipping synchronization checks as TSC is reliable.
[    1.243465] Booting processor 7 APIC 0x7 ip 0x6000
[    1.253721] Initializing CPU#7
[    1.401653] Calibrating delay using timer specific routine.. 5345.37 BogoMIPS (lpj=26726876)
[    1.401660] CPU: Physical Processor ID: 0
[    1.401661] CPU: Processor Core ID: 3
[    1.401663] CPU: L1 I cache: 32K, L1 D cache: 32K
[    1.401664] CPU: L2 cache: 256K
[    1.401665] CPU: L3 cache: 8192K
[    1.401667] CPU 7/0x7 -> Node 0
[    1.401669] mce: CPU supports 9 MCE banks
[    1.401677] CPU7: Thermal monitoring enabled (TM1)
[    1.401680] CPU 7 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
[    1.402499] x86 PAT enabled: cpu 7, old 0x7040600070406, new 0x7010600070106
[    1.403417] CPU7: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    1.403424] Skipping synchronization checks as TSC is reliable.
[    1.403439] Brought up 8 CPUs
[    1.403441] Total of 8 processors activated (42610.67 BogoMIPS).
[    1.403492] CPU0 attaching sched-domain:
[    1.403494]  domain 0: span 0,4 level SIBLING
[    1.403495]   groups: 0 4
[    1.403498]   domain 1: span 0-7 level MC
[    1.403500]    groups: 0,4 1,5 2,6 3,7
[    1.403504] CPU1 attaching sched-domain:
[    1.403505]  domain 0: span 1,5 level SIBLING
[    1.403506]   groups: 1 5
[    1.403509]   domain 1: span 0-7 level MC
[    1.403510]    groups: 1,5 2,6 3,7 0,4
[    1.403514] CPU2 attaching sched-domain:
[    1.403515]  domain 0: span 2,6 level SIBLING
[    1.403516]   groups: 2 6
[    1.403518]   domain 1: span 0-7 level MC
[    1.403519]    groups: 2,6 3,7 0,4 1,5
[    1.403523] CPU3 attaching sched-domain:
[    1.403524]  domain 0: span 3,7 level SIBLING
[    1.403526]   groups: 3 7
[    1.403528]   domain 1: span 0-7 level MC
[    1.403529]    groups: 3,7 0,4 1,5 2,6
[    1.403533] CPU4 attaching sched-domain:
[    1.403534]  domain 0: span 0,4 level SIBLING
[    1.403535]   groups: 4 0
[    1.403537]   domain 1: span 0-7 level MC
[    1.403538]    groups: 0,4 1,5 2,6 3,7
[    1.403542] CPU5 attaching sched-domain:
[    1.403543]  domain 0: span 1,5 level SIBLING
[    1.403544]   groups: 5 1
[    1.403547]   domain 1: span 0-7 level MC
[    1.403548]    groups: 1,5 2,6 3,7 0,4
[    1.403551] CPU6 attaching sched-domain:
[    1.403553]  domain 0: span 2,6 level SIBLING
[    1.403554]   groups: 6 2
[    1.403556]   domain 1: span 0-7 level MC
[    1.403557]    groups: 2,6 3,7 0,4 1,5
[    1.403561] CPU7 attaching sched-domain:
[    1.403562]  domain 0: span 3,7 level SIBLING
[    1.403563]   groups: 7 3
[    1.403565]   domain 1: span 0-7 level MC
[    1.403567]    groups: 3,7 0,4 1,5 2,6
[    1.403896] Booting paravirtualized kernel on bare hardware
[    1.404029] regulator: core version 0.5
[    1.404051] Time: 18:33:50  Date: 05/09/10
[    1.404086] NET: Registered protocol family 16
[    1.404168] ACPI: bus type pci registered
[    1.404220] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    1.404222] PCI: Not using MMCONFIG.
[    1.404223] PCI: Using configuration type 1 for base access
[    1.404810] bio: create slab <bio-0> at 0
[    1.405608] ACPI: EC: Look up EC in DSDT
[    1.438193] ACPI: Interpreter enabled
[    1.438198] ACPI: (supports S0 S1 S3 S4 S5)
[    1.438217] ACPI: Using IOAPIC for interrupt routing
[    1.438271] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    1.440412] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    1.445255] PCI: Using MMCONFIG at e0000000 - efffffff
[    1.452897] ACPI Warning: Incorrect checksum in table [OEMB] - 8B, should be 83 20090521 tbutils-246
[    1.453024] ACPI: No dock devices found.
[    1.453152] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.453220] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    1.453223] pci 0000:00:00.0: PME# disabled
[    1.453275] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.453278] pci 0000:00:01.0: PME# disabled
[    1.453329] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    1.453331] pci 0000:00:03.0: PME# disabled
[    1.453386] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    1.453388] pci 0000:00:07.0: PME# disabled
[    1.453673] pci 0000:00:1a.0: reg 20 io port: [0x9800-0x981f]
[    1.453734] pci 0000:00:1a.1: reg 20 io port: [0x9880-0x989f]
[    1.453794] pci 0000:00:1a.2: reg 20 io port: [0x9c00-0x9c1f]
[    1.453859] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf7fff000-0xf7fff3ff]
[    1.453907] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    1.453910] pci 0000:00:1a.7: PME# disabled
[    1.453946] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf7ff8000-0xf7ffbfff]
[    1.453982] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.453985] pci 0000:00:1b.0: PME# disabled
[    1.454035] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.454038] pci 0000:00:1c.0: PME# disabled
[    1.454091] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.454093] pci 0000:00:1c.2: PME# disabled
[    1.454145] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.454148] pci 0000:00:1c.3: PME# disabled
[    1.454200] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.454202] pci 0000:00:1c.4: PME# disabled
[    1.454252] pci 0000:00:1d.0: reg 20 io port: [0x9080-0x909f]
[    1.454313] pci 0000:00:1d.1: reg 20 io port: [0x9400-0x941f]
[    1.454374] pci 0000:00:1d.2: reg 20 io port: [0x9480-0x949f]
[    1.454438] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf7ffe000-0xf7ffe3ff]
[    1.454487] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.454490] pci 0000:00:1d.7: PME# disabled
[    1.454597] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    1.454600] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    1.454602] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    1.454607] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 4700 (mask 001f)
[    1.454653] pci 0000:00:1f.2: reg 10 io port: [0x8000-0x8007]
[    1.454658] pci 0000:00:1f.2: reg 14 io port: [0x7c00-0x7c03]
[    1.454662] pci 0000:00:1f.2: reg 18 io port: [0x7880-0x7887]
[    1.454667] pci 0000:00:1f.2: reg 1c io port: [0x7800-0x7803]
[    1.454672] pci 0000:00:1f.2: reg 20 io port: [0x7480-0x748f]
[    1.454676] pci 0000:00:1f.2: reg 24 io port: [0x7400-0x740f]
[    1.454716] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf7ffd000-0xf7ffd0ff]
[    1.454727] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    1.454765] pci 0000:00:1f.5: reg 10 io port: [0x9000-0x9007]
[    1.454769] pci 0000:00:1f.5: reg 14 io port: [0x8c00-0x8c03]
[    1.454774] pci 0000:00:1f.5: reg 18 io port: [0x8880-0x8887]
[    1.454778] pci 0000:00:1f.5: reg 1c io port: [0x8800-0x8803]
[    1.454783] pci 0000:00:1f.5: reg 20 io port: [0x8480-0x848f]
[    1.454787] pci 0000:00:1f.5: reg 24 io port: [0x8400-0x840f]
[    1.454863] pci 0000:02:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    1.454870] pci 0000:02:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    1.454877] pci 0000:02:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
[    1.454882] pci 0000:02:00.0: reg 24 io port: [0xac00-0xac7f]
[    1.454886] pci 0000:02:00.0: reg 30 32bit mmio: [0xfbb80000-0xfbbfffff]
[    1.454929] pci 0000:00:03.0: bridge io port: [0xa000-0xafff]
[    1.454932] pci 0000:00:03.0: bridge 32bit mmio: [0xf8000000-0xfbbfffff]
[    1.454936] pci 0000:00:03.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    1.455000] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf6e00000-0xf6efffff]
[    1.455042] pci 0000:06:00.0: reg 10 io port: [0xd800-0xd8ff]
[    1.455060] pci 0000:06:00.0: reg 18 64bit mmio: [0xfbeff000-0xfbefffff]
[    1.455073] pci 0000:06:00.0: reg 20 64bit mmio: [0xf6df0000-0xf6dfffff]
[    1.455080] pci 0000:06:00.0: reg 30 32bit mmio: [0xfbec0000-0xfbedffff]
[    1.455116] pci 0000:06:00.0: supports D1 D2
[    1.455117] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.455121] pci 0000:06:00.0: PME# disabled
[    1.455174] pci 0000:00:1c.2: bridge io port: [0xd000-0xdfff]
[    1.455177] pci 0000:00:1c.2: bridge 32bit mmio: [0xfbe00000-0xfbefffff]
[    1.455181] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xf6d00000-0xf6dfffff]
[    1.455229] pci 0000:05:00.0: reg 10 64bit mmio: [0xfbdff000-0xfbdff7ff]
[    1.455236] pci 0000:05:00.0: reg 18 io port: [0xc800-0xc8ff]
[    1.455289] pci 0000:05:00.0: supports D2
[    1.455290] pci 0000:05:00.0: PME# supported from D2 D3hot D3cold
[    1.455294] pci 0000:05:00.0: PME# disabled
[    1.455339] pci 0000:00:1c.3: bridge io port: [0xc000-0xcfff]
[    1.455343] pci 0000:00:1c.3: bridge 32bit mmio: [0xfbd00000-0xfbdfffff]
[    1.455429] pci 0000:04:00.0: reg 24 32bit mmio: [0xfbcfe000-0xfbcfffff]
[    1.455437] pci 0000:04:00.0: reg 30 32bit mmio: [0xfbce0000-0xfbceffff]
[    1.455466] pci 0000:04:00.0: PME# supported from D3hot
[    1.455471] pci 0000:04:00.0: PME# disabled
[    1.455520] pci 0000:04:00.1: reg 10 io port: [0xbc00-0xbc07]
[    1.455528] pci 0000:04:00.1: reg 14 io port: [0xb880-0xb883]
[    1.455536] pci 0000:04:00.1: reg 18 io port: [0xb800-0xb807]
[    1.455544] pci 0000:04:00.1: reg 1c io port: [0xb480-0xb483]
[    1.455552] pci 0000:04:00.1: reg 20 io port: [0xb400-0xb40f]
[    1.455635] pci 0000:00:1c.4: bridge io port: [0xb000-0xbfff]
[    1.455638] pci 0000:00:1c.4: bridge 32bit mmio: [0xfbc00000-0xfbcfffff]
[    1.455661] pci 0000:08:00.0: reg 10 32bit mmio: [0xf6ffe000-0xf6ffefff]
[    1.455708] pci 0000:08:00.1: reg 10 32bit mmio: [0xf6fff000-0xf6ffffff]
[    1.455773] pci 0000:08:01.0: reg 10 io port: [0xec00-0xec3f]
[    1.455815] pci 0000:08:01.0: supports D2
[    1.455856] pci 0000:00:1e.0: transparent bridge
[    1.455859] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    1.455865] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xf6f00000-0xf6ffffff]
[    1.455895] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.456135] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.456228] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    1.456281] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    1.456331] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    1.456379] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    1.456442] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE1._PRT]
[    1.456491] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE3._PRT]
[    1.456541] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE7._PRT]
[    1.481447] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12 14 *15)
[    1.481557] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    1.481666] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12 14 15)
[    1.481773] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *10 11 12 14 15)
[    1.481879] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 *14 15)
[    1.481984] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 6 7 10 11 12 14 15)
[    1.482090] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
[    1.482197] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 6 7 10 11 12 14 15)
[    1.482325] SCSI subsystem initialized
[    1.482424] libata version 3.00 loaded.
[    1.482471] usbcore: registered new interface driver usbfs
[    1.482481] usbcore: registered new interface driver hub
[    1.482496] usbcore: registered new device driver usb
[    1.482586] ACPI: WMI: Mapper loaded
[    1.482587] PCI: Using ACPI for IRQ routing
[    1.521628] Bluetooth: Core ver 2.15
[    1.521656] NET: Registered protocol family 31
[    1.521658] Bluetooth: HCI device and connection manager initialized
[    1.521661] Bluetooth: HCI socket layer initialized
[    1.521663] NetLabel: Initializing
[    1.521664] NetLabel:  domain hash size = 128
[    1.521666] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.521679] NetLabel:  unlabeled traffic allowed by default
[    1.521733] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    1.521736] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    1.581621] Switched to high resolution mode on CPU 0
[    1.582860] Switched to high resolution mode on CPU 3
[    1.582865] Switched to high resolution mode on CPU 1
[    1.582869] Switched to high resolution mode on CPU 2
[    1.583219] Switched to high resolution mode on CPU 4
[    1.583279] Switched to high resolution mode on CPU 6
[    1.583283] Switched to high resolution mode on CPU 5
[    1.583288] Switched to high resolution mode on CPU 7
[    1.601618] pnp: PnP ACPI init
[    1.601633] ACPI: bus type pnp registered
[    1.604205] pnp: PnP ACPI: found 15 devices
[    1.604207] ACPI: ACPI bus type pnp unregistered
[    1.604215] system 00:01: iomem range 0xfbf00000-0xfbffffff has been reserved
[    1.604217] system 00:01: iomem range 0xfc000000-0xfcffffff has been reserved
[    1.604218] system 00:01: iomem range 0xfd000000-0xfdffffff has been reserved
[    1.604220] system 00:01: iomem range 0xfe000000-0xfebfffff has been reserved
[    1.604222] system 00:01: iomem range 0xfec8a000-0xfec8afff could not be reserved
[    1.604224] system 00:01: iomem range 0xfed10000-0xfed10fff has been reserved
[    1.604229] system 00:07: ioport range 0x290-0x29f has been reserved
[    1.604232] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    1.604234] system 00:08: ioport range 0x800-0x87f has been reserved
[    1.604236] system 00:08: ioport range 0x500-0x57f could not be reserved
[    1.604238] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.604239] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    1.604241] system 00:08: iomem range 0xfed40000-0xfed8ffff has been reserved
[    1.604245] system 00:0b: iomem range 0xffc00000-0xffdfffff has been reserved
[    1.604248] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    1.604250] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.604253] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    1.604256] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    1.604258] system 00:0e: iomem range 0xc0000-0xcffff has been reserved
[    1.604260] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    1.604262] system 00:0e: iomem range 0x100000-0xbfefffff could not be reserved
[    1.604263] system 00:0e: iomem range 0xfed90000-0xffffffff could not be reserved
[    1.608881] AppArmor: AppArmor Filesystem Enabled
[    1.608944] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.608945] pci 0000:00:01.0:   IO window: disabled
[    1.608948] pci 0000:00:01.0:   MEM window: disabled
[    1.608951] pci 0000:00:01.0:   PREFETCH window: disabled
[    1.608954] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
[    1.608956] pci 0000:00:03.0:   IO window: 0xa000-0xafff
[    1.608959] pci 0000:00:03.0:   MEM window: 0xf8000000-0xfbbfffff
[    1.608962] pci 0000:00:03.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    1.608966] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    1.608967] pci 0000:00:07.0:   IO window: disabled
[    1.608970] pci 0000:00:07.0:   MEM window: disabled
[    1.608973] pci 0000:00:07.0:   PREFETCH window: disabled
[    1.608975] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:07
[    1.608976] pci 0000:00:1c.0:   IO window: disabled
[    1.608980] pci 0000:00:1c.0:   MEM window: disabled
[    1.608983] pci 0000:00:1c.0:   PREFETCH window: 0x000000f6e00000-0x000000f6efffff
[    1.608988] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
[    1.608990] pci 0000:00:1c.2:   IO window: 0xd000-0xdfff
[    1.608993] pci 0000:00:1c.2:   MEM window: 0xfbe00000-0xfbefffff
[    1.608996] pci 0000:00:1c.2:   PREFETCH window: 0x000000f6d00000-0x000000f6dfffff
[    1.609001] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    1.609003] pci 0000:00:1c.3:   IO window: 0xc000-0xcfff
[    1.609007] pci 0000:00:1c.3:   MEM window: 0xfbd00000-0xfbdfffff
[    1.609009] pci 0000:00:1c.3:   PREFETCH window: disabled
[    1.609013] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:04
[    1.609015] pci 0000:00:1c.4:   IO window: 0xb000-0xbfff
[    1.609018] pci 0000:00:1c.4:   MEM window: 0xfbc00000-0xfbcfffff
[    1.609021] pci 0000:00:1c.4:   PREFETCH window: disabled
[    1.609024] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
[    1.609026] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    1.609030] pci 0000:00:1e.0:   MEM window: disabled
[    1.609033] pci 0000:00:1e.0:   PREFETCH window: 0x000000f6f00000-0x000000f6ffffff
[    1.609043] pci 0000:00:01.0: setting latency timer to 64
[    1.609049] pci 0000:00:03.0: setting latency timer to 64
[    1.609054] pci 0000:00:07.0: setting latency timer to 64
[    1.609061]   alloc irq_desc for 17 on node 0
[    1.609062]   alloc kstat_irqs on node 0
[    1.609066] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.609069] pci 0000:00:1c.0: setting latency timer to 64
[    1.609076]   alloc irq_desc for 18 on node 0
[    1.609077]   alloc kstat_irqs on node 0
[    1.609080] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.609083] pci 0000:00:1c.2: setting latency timer to 64
[    1.609088]   alloc irq_desc for 19 on node 0
[    1.609089]   alloc kstat_irqs on node 0
[    1.609091] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.609094] pci 0000:00:1c.3: setting latency timer to 64
[    1.609100] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.609102] pci 0000:00:1c.4: setting latency timer to 64
[    1.609107] pci 0000:00:1e.0: setting latency timer to 64
[    1.609110] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    1.609112] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    1.609114] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    1.609115] pci_bus 0000:02: resource 1 mem: [0xf8000000-0xfbbfffff]
[    1.609117] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xdfffffff]
[    1.609119] pci_bus 0000:07: resource 2 pref mem [0xf6e00000-0xf6efffff]
[    1.609120] pci_bus 0000:06: resource 0 io:  [0xd000-0xdfff]
[    1.609122] pci_bus 0000:06: resource 1 mem: [0xfbe00000-0xfbefffff]
[    1.609123] pci_bus 0000:06: resource 2 pref mem [0xf6d00000-0xf6dfffff]
[    1.609125] pci_bus 0000:05: resource 0 io:  [0xc000-0xcfff]
[    1.609126] pci_bus 0000:05: resource 1 mem: [0xfbd00000-0xfbdfffff]
[    1.609128] pci_bus 0000:04: resource 0 io:  [0xb000-0xbfff]
[    1.609129] pci_bus 0000:04: resource 1 mem: [0xfbc00000-0xfbcfffff]
[    1.609131] pci_bus 0000:08: resource 0 io:  [0xe000-0xefff]
[    1.609132] pci_bus 0000:08: resource 2 pref mem [0xf6f00000-0xf6ffffff]
[    1.609134] pci_bus 0000:08: resource 3 io:  [0x00-0xffff]
[    1.609135] pci_bus 0000:08: resource 4 mem: [0x000000-0xffffffffffffffff]
[    1.609162] NET: Registered protocol family 2
[    1.609448] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    1.610382] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.611589] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.611739] TCP: Hash tables configured (established 524288 bind 65536)
[    1.611740] TCP reno registered
[    1.611825] NET: Registered protocol family 1
[    1.611863] Trying to unpack rootfs image as initramfs...
[    1.738221] Freeing initrd memory: 7559k freed
[    1.739614] Scanning for low memory corruption every 60 seconds
[    1.739694] audit: initializing netlink socket (disabled)
[    1.739703] type=2000 audit(1273430029.570:1): initialized
[    1.747792] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.748798] VFS: Disk quotas dquot_6.5.2
[    1.748836] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.749255] fuse init (API version 7.12)
[    1.749311] msgmni has been set to 24067
[    1.749490] alg: No test for stdrng (krng)
[    1.749496] io scheduler noop registered
[    1.749498] io scheduler anticipatory registered
[    1.749499] io scheduler deadline registered
[    1.749529] io scheduler cfq registered (default)
[    1.749667] pci 0000:02:00.0: Boot video device
[    1.749785]   alloc irq_desc for 48 on node 0
[    1.749787]   alloc kstat_irqs on node 0
[    1.749794] pcieport-driver 0000:00:01.0: irq 48 for MSI/MSI-X
[    1.749800] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.749904]   alloc irq_desc for 49 on node 0
[    1.749905]   alloc kstat_irqs on node 0
[    1.749911] pcieport-driver 0000:00:03.0: irq 49 for MSI/MSI-X
[    1.749916] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.750015]   alloc irq_desc for 50 on node 0
[    1.750017]   alloc kstat_irqs on node 0
[    1.750022] pcieport-driver 0000:00:07.0: irq 50 for MSI/MSI-X
[    1.750027] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.750124]   alloc irq_desc for 51 on node 0
[    1.750126]   alloc kstat_irqs on node 0
[    1.750131] pcieport-driver 0000:00:1c.0: irq 51 for MSI/MSI-X
[    1.750138] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.750245]   alloc irq_desc for 52 on node 0
[    1.750246]   alloc kstat_irqs on node 0
[    1.750252] pcieport-driver 0000:00:1c.2: irq 52 for MSI/MSI-X
[    1.750258] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.750364]   alloc irq_desc for 53 on node 0
[    1.750365]   alloc kstat_irqs on node 0
[    1.750371] pcieport-driver 0000:00:1c.3: irq 53 for MSI/MSI-X
[    1.750377] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.750481]   alloc irq_desc for 54 on node 0
[    1.750482]   alloc kstat_irqs on node 0
[    1.750488] pcieport-driver 0000:00:1c.4: irq 54 for MSI/MSI-X
[    1.750494] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.750566] aer 0000:00:01.0:pcie02: AER service couldn't init device: no _OSC support
[    1.750572] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support
[    1.750575] aer 0000:00:07.0:pcie02: AER service couldn't init device: no _OSC support
[    1.750581] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.750675] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.750750] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.750752] ACPI: Power Button [PWRF]
[    1.750789] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.750791] ACPI: Power Button [PWRB]
[    1.751493] ACPI: SSDT 00000000bf6980c0 00403 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    1.751750] processor LNXCPU:00: registered as cooling_device0
[    1.752137] ACPI: SSDT 00000000bf6984d0 00403 (v01 DpgPmm  P002Ist 00000012 INTL 20060113)
[    1.752380] processor LNXCPU:01: registered as cooling_device1
[    1.752761] ACPI: SSDT 00000000bf6988e0 00403 (v01 DpgPmm  P003Ist 00000012 INTL 20060113)
[    1.753009] processor LNXCPU:02: registered as cooling_device2
[    1.753384] ACPI: SSDT 00000000bf698cf0 00403 (v01 DpgPmm  P004Ist 00000012 INTL 20060113)
[    1.753632] processor LNXCPU:03: registered as cooling_device3
[    1.754020] ACPI: SSDT 00000000bf699100 00403 (v01 DpgPmm  P005Ist 00000012 INTL 20060113)
[    1.754268] processor LNXCPU:04: registered as cooling_device4
[    1.754650] ACPI: SSDT 00000000bf699510 00403 (v01 DpgPmm  P006Ist 00000012 INTL 20060113)
[    1.754893] processor LNXCPU:05: registered as cooling_device5
[    1.755269] ACPI: SSDT 00000000bf699920 00403 (v01 DpgPmm  P007Ist 00000012 INTL 20060113)
[    1.755515] processor LNXCPU:06: registered as cooling_device6
[    1.755903] ACPI: SSDT 00000000bf699d30 00403 (v01 DpgPmm  P008Ist 00000012 INTL 20060113)
[    1.756150] processor LNXCPU:07: registered as cooling_device7
[    1.758941] Linux agpgart interface v0.103
[    1.758947] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.759746] brd: module loaded
[    1.760035] loop: module loaded
[    1.760076] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.760145] ahci 0000:04:00.0: version 3.0
[    1.760157]   alloc irq_desc for 16 on node 0
[    1.760158]   alloc kstat_irqs on node 0
[    1.760163] ahci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.771571] ahci 0000:04:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.771575] ahci 0000:04:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.771581] ahci 0000:04:00.0: setting latency timer to 64
[    1.771678] scsi0 : ahci
[    1.771728] scsi1 : ahci
[    1.771776] ata1: SATA max UDMA/133 abar m8192@0xfbcfe000 port 0xfbcfe100 irq 16
[    1.771779] ata2: SATA max UDMA/133 abar m8192@0xfbcfe000 port 0xfbcfe180 irq 16
[    1.771828] ata_piix 0000:00:1f.2: version 2.13
[    1.771836]   alloc irq_desc for 20 on node 0
[    1.771837]   alloc kstat_irqs on node 0
[    1.771840] ata_piix 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.771844] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.771868] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.771901] scsi2 : ata_piix
[    1.771934] scsi3 : ata_piix
[    1.773014] ata3: SATA max UDMA/133 cmd 0x8000 ctl 0x7c00 bmdma 0x7480 irq 20
[    1.773018] ata4: SATA max UDMA/133 cmd 0x7880 ctl 0x7800 bmdma 0x7488 irq 20
[    1.773060] ata_piix 0000:00:1f.5: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.773063] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.773086] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.773110] scsi4 : ata_piix
[    1.773144] scsi5 : ata_piix
[    1.774116] ata5: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8480 irq 20
[    1.774120] ata6: SATA max UDMA/133 cmd 0x8880 ctl 0x8800 bmdma 0x8488 irq 20
[    1.774360] pata_jmicron 0000:04:00.1: enabling device (0000 -> 0001)
[    1.774364] pata_jmicron 0000:04:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.774383] pata_jmicron 0000:04:00.1: setting latency timer to 64
[    1.774421] scsi6 : pata_jmicron
[    1.774454] scsi7 : pata_jmicron
[    1.775024] ata7: PATA max UDMA/100 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 17
[    1.775026] ata8: PATA max UDMA/100 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 17
[    1.775354] Fixed MDIO Bus: probed
[    1.775374] PPP generic driver version 2.4.2
[    1.775425] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.775461] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.775472] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.775476] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.775509] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.779412] ehci_hcd 0000:00:1a.7: debug port 1
[    1.779417] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.779426] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf7fff000
[    1.801530] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.801602] usb usb1: configuration #1 chosen from 1 choice
[    1.801629] hub 1-0:1.0: USB hub found
[    1.801633] hub 1-0:1.0: 6 ports detected
[    1.801693]   alloc irq_desc for 23 on node 0
[    1.801695]   alloc kstat_irqs on node 0
[    1.801699] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.801707] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.801709] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.801732] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.805618] ehci_hcd 0000:00:1d.7: debug port 1
[    1.805623] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.805632] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7ffe000
[    1.821522] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.821582] usb usb2: configuration #1 chosen from 1 choice
[    1.821609] hub 2-0:1.0: USB hub found
[    1.821613] hub 2-0:1.0: 6 ports detected
[    1.821658] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.821668] uhci_hcd: USB Universal Host Controller Interface driver
[    1.821714] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.821718] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.821720] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.821742] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.821762] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00009800
[    1.821810] usb usb3: configuration #1 chosen from 1 choice
[    1.821826] hub 3-0:1.0: USB hub found
[    1.821830] hub 3-0:1.0: 2 ports detected
[    1.821878]   alloc irq_desc for 21 on node 0
[    1.821882]   alloc kstat_irqs on node 0
[    1.821885] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.821890] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.821892] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.821912] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.821937] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00009880
[    1.821986] usb usb4: configuration #1 chosen from 1 choice
[    1.822001] hub 4-0:1.0: USB hub found
[    1.822004] hub 4-0:1.0: 2 ports detected
[    1.822051] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.822056] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.822058] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.822077] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.822103] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00009c00
[    1.822151] usb usb5: configuration #1 chosen from 1 choice
[    1.822167] hub 5-0:1.0: USB hub found
[    1.822170] hub 5-0:1.0: 2 ports detected
[    1.822217] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.822222] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.822224] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.822248] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.822268] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00009080
[    1.822316] usb usb6: configuration #1 chosen from 1 choice
[    1.822331] hub 6-0:1.0: USB hub found
[    1.822336] hub 6-0:1.0: 2 ports detected
[    1.822383] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.822388] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.822390] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.822410] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.822430] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00009400
[    1.822481] usb usb7: configuration #1 chosen from 1 choice
[    1.822496] hub 7-0:1.0: USB hub found
[    1.822500] hub 7-0:1.0: 2 ports detected
[    1.822545] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.822549] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.822551] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.822572] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.822592] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009480
[    1.822639] usb usb8: configuration #1 chosen from 1 choice
[    1.822656] hub 8-0:1.0: USB hub found
[    1.822659] hub 8-0:1.0: 2 ports detected
[    1.822727] PNP: No PS/2 controller found. Probing ports directly.
[    1.825058] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.825066] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.825112] mice: PS/2 mouse device common for all mice
[    1.825167] rtc_cmos 00:03: RTC can wake from S4
[    1.825188] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.825210] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.825279] device-mapper: uevent: version 1.0.3
[    1.825329] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.825417] device-mapper: multipath: version 1.1.0 loaded
[    1.825424] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.825654] cpuidle: using governor ladder
[    1.825656] cpuidle: using governor menu
[    1.825949] TCP cubic registered
[    1.826033] NET: Registered protocol family 10
[    1.826366] lo: Disabled Privacy Extensions
[    1.826561] NET: Registered protocol family 17
[    1.826574] Bluetooth: L2CAP ver 2.13
[    1.826575] Bluetooth: L2CAP socket layer initialized
[    1.826577] Bluetooth: SCO (Voice Link) ver 0.6
[    1.826578] Bluetooth: SCO socket layer initialized
[    1.826592] Bluetooth: RFCOMM TTY layer initialized
[    1.826594] Bluetooth: RFCOMM socket layer initialized
[    1.826595] Bluetooth: RFCOMM ver 1.11
[    1.828747] PM: Resume from disk failed.
[    1.828753] registered taskstats version 1
[    1.828881]   Magic number: 10:607:594
[    1.828936] rtc_cmos 00:03: setting system clock to 2010-05-09 18:33:50 UTC (1273430030)
[    1.828938] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.828939] EDD information not available.
[    2.131854] ata6: SATA link down (SStatus 0 SControl 300)
[    2.131905] ata2: SATA link down (SStatus 0 SControl 300)
[    2.131934] ata1: SATA link down (SStatus 0 SControl 300)
[    2.291366] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.313910] ata5.00: ATA-8: WDC WD6401AALS-00L3B2, 01.03B01, max UDMA/133
[    2.313914] ata5.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.331960] ata5.00: configured for UDMA/133
[    2.421277] usb 7-1: new low speed USB device using uhci_hcd and address 2
[    2.491822] ata3.00: SATA link down (SStatus 0 SControl 300)
[    2.491834] ata3.01: SATA link down (SStatus 0 SControl 300)
[    2.608243] usb 7-1: configuration #1 chosen from 1 choice
[    2.641245] ata4.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.641259] ata4.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.681387] ata4.00: ATAPI: TSSTcorp CDDVDW SH-S223F, SB03, max UDMA/100
[    2.681404] ata4.01: ATAPI: TSSTcorp CDDVDW SH-S223F, SB03, max UDMA/100
[    2.721381] ata4.00: configured for UDMA/100
[    2.761370] ata4.01: configured for UDMA/100
[    2.762591] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223F  SB03 PQ: 0 ANSI: 5
[    2.766139] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.766143] Uniform CD-ROM driver Revision: 3.20
[    2.766221] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.766253] sr 3:0:0:0: Attached scsi generic sg0 type 5
[    2.766880] scsi 3:0:1:0: CD-ROM            TSSTcorp CDDVDW SH-S223F  SB03 PQ: 0 ANSI: 5
[    2.770392] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.770463] sr 3:0:1:0: Attached scsi CD-ROM sr1
[    2.770498] sr 3:0:1:0: Attached scsi generic sg1 type 5
[    2.770555] scsi 4:0:0:0: Direct-Access     ATA      WDC WD6401AALS-0 01.0 PQ: 0 ANSI: 5
[    2.770620] sd 4:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    2.770623] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.770653] sd 4:0:0:0: [sda] Write Protect is off
[    2.770655] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.770667] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.770739]  sda: sda1 sda2 sda3 sda4
[    2.789788] sd 4:0:0:0: [sda] Attached SCSI disk
[    2.881093] usb 7-2: new low speed USB device using uhci_hcd and address 3
[    2.932329] Freeing unused kernel memory: 660k freed
[    2.932412] Write protecting the kernel read-only data: 7580k
[    2.970311] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.970328] r8169 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.970373] r8169 0000:06:00.0: setting latency timer to 64
[    2.970416]   alloc irq_desc for 55 on node 0
[    2.970418]   alloc kstat_irqs on node 0
[    2.970431] r8169 0000:06:00.0: irq 55 for MSI/MSI-X
[    2.970963] eth0: RTL8168c/8111c at 0xffffc90001874000, 00:24:8c:fc:81:b3, XID 3c4000c0 IRQ 55
[    2.971919] usbcore: registered new interface driver hiddev
[    2.974880] Floppy drive(s): fd0 is 1.44M
[    2.974947] ohci1394 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.974953] ohci1394 0000:05:00.0: setting latency timer to 64
[    2.985215] input: Microsoft Microsoft® Digital Media oard 3000 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input3
[    2.985253] generic-usb 0003:045E:0732.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft® Digital Media oard 3000] on usb-0000:00:1d.1-1/input0
[    3.005047] FDC 0 is a post-1991 82077
[    3.016185] input: Microsoft Microsoft® Digital Media oard 3000 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/input/input4
[    3.016214] generic-usb 0003:045E:0732.0002: input,hidraw1: USB HID v1.11 Device [Microsoft Microsoft® Digital Media oard 3000] on usb-0000:00:1d.1-1/input1
[    3.016223] usbcore: registered new interface driver usbhid
[    3.016225] usbhid: v2.6:USB HID core driver
[    3.043061] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fbdff000-fbdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.069095] usb 7-2: configuration #1 chosen from 1 choice
[    3.087160] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input5
[    3.087198] generic-usb 0003:045E:0040.0003: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.1-2/input0
[    3.421249] EXT4-fs (sda4): barriers enabled
[    3.434758] kjournald2 starting: pid 372, dev sda4:8, commit interval 5 seconds
[    3.434766] EXT4-fs (sda4): delayed allocation enabled
[    3.434770] EXT4-fs: file extents enabled
[    3.446080] EXT4-fs: mballoc enabled
[    3.446089] EXT4-fs (sda4): mounted filesystem with ordered data mode
[    4.360604] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001e59700]
[    5.834434] Adding 11711376k swap on /dev/sda3.  Priority:-1 extents:1 across:11711376k 
[    6.386017] EXT4-fs (sda4): internal journal on sda4:8
[    7.005385] udev: starting version 151
[    7.834793] type=1505 audit(1273448036.503:2): operation="profile_load" pid=3083 name=/sbin/dhclient3
[    7.835210] type=1505 audit(1273448036.503:3): operation="profile_load" pid=3083 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.835455] type=1505 audit(1273448036.503:4): operation="profile_load" pid=3083 name=/usr/lib/connman/scripts/dhclient-script
[    7.909874] lp: driver loaded but no devices found
[    8.720374] nvidia: module license 'NVIDIA' taints kernel.
[    8.720422] Disabling lock debugging due to kernel taint
[    8.973348]   alloc irq_desc for 24 on node 0
[    8.973351]   alloc kstat_irqs on node 0
[    8.973357] nvidia 0000:02:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[    8.973409] nvidia 0000:02:00.0: setting latency timer to 64
[    8.973524] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010
[    9.224457] Linux video capture interface: v2.00
[    9.309792] bttv: driver version 0.9.18 loaded
[    9.309836] bttv: using 8 buffers with 2080k (520 pages) each for capture
[    9.309943] bttv: Bt8xx card found (0).
[    9.309992] bttv 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.310044] bttv0: Bt878 (rev 2) at 0000:08:00.0, irq: 16, latency: 64, mmio: 0xf6ffe000
[    9.310148] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[    9.310197] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[    9.310242] IRQ 16/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.310310] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[    9.312813] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[    9.345990] tveeprom 0-0050: Hauppauge model 61381, rev D123, serial# 1820652
[    9.346052] tveeprom 0-0050: tuner model is Philips FM1236 (idx 23, type 2)
[    9.346112] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[    9.346170] tveeprom 0-0050: audio processor is MSP3430 (idx 7)
[    9.346228] tveeprom 0-0050: has radio
[    9.346283] bttv0: Hauppauge eeprom indicates model#61381
[    9.346340] bttv0: tuner type=2
[    9.391723] msp3400 0-0040: MSP3430G-A1 found @ 0x80 (bt878 #0 [sw])
[    9.391783] msp3400 0-0040: msp3400 supports radio, mode is autodetect and autoselect
[    9.463887] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[    9.611361] tuner-simple 0-0061: creating new instance
[    9.611422] tuner-simple 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[    9.612188] bttv0: registered device video0
[    9.612257] bttv0: registered device vbi0
[    9.612328] bttv0: registered device radio0
[    9.631125] bttv0: PLL: 28636363 => 35468950 .. ok
[    9.888102] Bt87x 0000:08:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.888243] bt87x0: Using board 1, analog, digital (rate 32000 Hz)
[   10.299267]   alloc irq_desc for 22 on node 0
[   10.299270]   alloc kstat_irqs on node 0
[   10.299275] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.299385] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.391772] ENS1371 0000:08:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.675067] hda_codec: Unknown model for ALC1200, trying auto-probe from BIOS...
[   10.675349] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   11.871779] r8169: eth0: link up
[   11.871838] r8169: eth0: link up
[   12.540363] type=1505 audit(1273448041.213:5): operation="profile_load" pid=3359 name=/usr/share/gdm/guest-session/Xsession
[   12.541495] type=1505 audit(1273448041.213:6): operation="profile_replace" pid=3554 name=/sbin/dhclient3
[   12.541927] type=1505 audit(1273448041.213:7): operation="profile_replace" pid=3554 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   12.542198] type=1505 audit(1273448041.213:8): operation="profile_replace" pid=3554 name=/usr/lib/connman/scripts/dhclient-script
[   12.783256] type=1505 audit(1273448041.453:9): operation="profile_load" pid=3556 name=/usr/bin/evince
[   12.787805] type=1505 audit(1273448041.463:10): operation="profile_load" pid=3556 name=/usr/bin/evince-previewer
[   12.790723] type=1505 audit(1273448041.463:11): operation="profile_load" pid=3556 name=/usr/bin/evince-thumbnailer
[   13.166750] type=1505 audit(1273448041.832:12): operation="profile_load" pid=3561 name=/usr/lib/cups/backend/cups-pdf
[   13.167249] type=1505 audit(1273448041.842:13): operation="profile_load" pid=3561 name=/usr/sbin/cupsd
[   13.188462] type=1505 audit(1273448041.863:14): operation="profile_load" pid=3564 name=/usr/sbin/mysqld
[   13.268425] type=1505 audit(1273448041.943:15): operation="profile_load" pid=3565 name=/usr/sbin/mysqld-akonadi
[   13.295924] type=1505 audit(1273448041.963:16): operation="profile_load" pid=3570 name=/usr/sbin/tcpdump
[   17.351496] ppdev: user-space parallel port driver
[   19.578939] CPU0 attaching NULL sched-domain.
[   19.578942] CPU1 attaching NULL sched-domain.
[   19.578944] CPU2 attaching NULL sched-domain.
[   19.578945] CPU3 attaching NULL sched-domain.
[   19.578947] CPU4 attaching NULL sched-domain.
[   19.578948] CPU5 attaching NULL sched-domain.
[   19.578949] CPU6 attaching NULL sched-domain.
[   19.578950] CPU7 attaching NULL sched-domain.
[   19.624451] CPU0 attaching sched-domain:
[   19.624455]  domain 0: span 0,4 level SIBLING
[   19.624458]   groups: 0 4
[   19.624462]   domain 1: span 0-7 level MC
[   19.624465]    groups: 0,4 1,5 2,6 3,7
[   19.624471] CPU1 attaching sched-domain:
[   19.624476]  domain 0: span 1,5 level SIBLING
[   19.624477]   groups: 1 5
[   19.624479]   domain 1: span 0-7 level MC
[   19.624480]    groups: 1,5 2,6 3,7 0,4
[   19.624484] CPU2 attaching sched-domain:
[   19.624485]  domain 0: span 2,6 level SIBLING
[   19.624486]   groups: 2 6
[   19.624488]   domain 1: span 0-7 level MC
[   19.624489]    groups: 2,6 3,7 0,4 1,5
[   19.624493] CPU3 attaching sched-domain:
[   19.624494]  domain 0: span 3,7 level SIBLING
[   19.624495]   groups: 3 7
[   19.624497]   domain 1: span 0-7 level MC
[   19.624498]    groups: 3,7 0,4 1,5 2,6
[   19.624502] CPU4 attaching sched-domain:
[   19.624503]  domain 0: span 0,4 level SIBLING
[   19.624504]   groups: 4 0
[   19.624506]   domain 1: span 0-7 level MC
[   19.624507]    groups: 0,4 1,5 2,6 3,7
[   19.624511] CPU5 attaching sched-domain:
[   19.624512]  domain 0: span 1,5 level SIBLING
[   19.624513]   groups: 5 1
[   19.624515]   domain 1: span 0-7 level MC
[   19.624516]    groups: 1,5 2,6 3,7 0,4
[   19.624519] CPU6 attaching sched-domain:
[   19.624521]  domain 0: span 2,6 level SIBLING
[   19.624522]   groups: 6 2
[   19.624524]   domain 1: span 0-7 level MC
[   19.624525]    groups: 2,6 3,7 0,4 1,5
[   19.624528] CPU7 attaching sched-domain:
[   19.624530]  domain 0: span 3,7 level SIBLING
[   19.624531]   groups: 7 3
[   19.624533]   domain 1: span 0-7 level MC
[   19.624534]    groups: 3,7 0,4 1,5 2,6
[   19.625008] CPU0 attaching NULL sched-domain.
[   19.625010] CPU1 attaching NULL sched-domain.
[   19.625011] CPU2 attaching NULL sched-domain.
[   19.625012] CPU3 attaching NULL sched-domain.
[   19.625013] CPU4 attaching NULL sched-domain.
[   19.625014] CPU5 attaching NULL sched-domain.
[   19.625016] CPU6 attaching NULL sched-domain.
[   19.625017] CPU7 attaching NULL sched-domain.
[   19.664427] CPU0 attaching sched-domain:
[   19.664429]  domain 0: span 0,4 level SIBLING
[   19.664430]   groups: 0 4
[   19.664432]   domain 1: span 0-7 level MC
[   19.664434]    groups: 0,4 1,5 2,6 3,7
[   19.664437] CPU1 attaching sched-domain:
[   19.664438]  domain 0: span 1,5 level SIBLING
[   19.664440]   groups: 1 5
[   19.664442]   domain 1: span 0-7 level MC
[   19.664443]    groups: 1,5 2,6 3,7 0,4
[   19.664446] CPU2 attaching sched-domain:
[   19.664447]  domain 0: span 2,6 level SIBLING
[   19.664449]   groups: 2 6
[   19.664451]   domain 1: span 0-7 level MC
[   19.664452]    groups: 2,6 3,7 0,4 1,5
[   19.664455] CPU3 attaching sched-domain:
[   19.664456]  domain 0: span 3,7 level SIBLING
[   19.664458]   groups: 3 7
[   19.664460]   domain 1: span 0-7 level MC
[   19.664461]    groups: 3,7 0,4 1,5 2,6
[   19.664464] CPU4 attaching sched-domain:
[   19.664465]  domain 0: span 0,4 level SIBLING
[   19.664467]   groups: 4 0
[   19.664469]   domain 1: span 0-7 level MC
[   19.664470]    groups: 0,4 1,5 2,6 3,7
[   19.664473] CPU5 attaching sched-domain:
[   19.664474]  domain 0: span 1,5 level SIBLING
[   19.664476]   groups: 5 1
[   19.664478]   domain 1: span 0-7 level MC
[   19.664479]    groups: 1,5 2,6 3,7 0,4
[   19.664482] CPU6 attaching sched-domain:
[   19.664483]  domain 0: span 2,6 level SIBLING
[   19.664484]   groups: 6 2
[   19.664486]   domain 1: span 0-7 level MC
[   19.664488]    groups: 2,6 3,7 0,4 1,5
[   19.664491] CPU7 attaching sched-domain:
[   19.664492]  domain 0: span 3,7 level SIBLING
[   19.664493]   groups: 7 3
[   19.664495]   domain 1: span 0-7 level MC
[   19.664496]    groups: 3,7 0,4 1,5 2,6
[   21.763873] CPU0 attaching NULL sched-domain.
[   21.763877] CPU1 attaching NULL sched-domain.
[   21.763879] CPU2 attaching NULL sched-domain.
[   21.763880] CPU3 attaching NULL sched-domain.
[   21.763881] CPU4 attaching NULL sched-domain.
[   21.763882] CPU5 attaching NULL sched-domain.
[   21.763883] CPU6 attaching NULL sched-domain.
[   21.763885] CPU7 attaching NULL sched-domain.
[   21.793103] CPU0 attaching sched-domain:
[   21.793107]  domain 0: span 0,4 level SIBLING
[   21.793109]   groups: 0 4
[   21.793114]   domain 1: span 0-7 level MC
[   21.793116]    groups: 0,4 1,5 2,6 3,7
[   21.793125] CPU1 attaching sched-domain:
[   21.793126]  domain 0: span 1,5 level SIBLING
[   21.793127]   groups: 1 5
[   21.793129]   domain 1: span 0-7 level MC
[   21.793131]    groups: 1,5 2,6 3,7 0,4
[   21.793134] CPU2 attaching sched-domain:
[   21.793135]  domain 0: span 2,6 level SIBLING
[   21.793136]   groups: 2 6
[   21.793138]   domain 1: span 0-7 level MC
[   21.793140]    groups: 2,6 3,7 0,4 1,5
[   21.793143] CPU3 attaching sched-domain:
[   21.793144]  domain 0: span 3,7 level SIBLING
[   21.793145]   groups: 3 7
[   21.793147]   domain 1: span 0-7 level MC
[   21.793149]    groups: 3,7 0,4 1,5 2,6
[   21.793152] CPU4 attaching sched-domain:
[   21.793153]  domain 0: span 0,4 level SIBLING
[   21.793154]   groups: 4 0
[   21.793156]   domain 1: span 0-7 level MC
[   21.793157]    groups: 0,4 1,5 2,6 3,7
[   21.793161] CPU5 attaching sched-domain:
[   21.793162]  domain 0: span 1,5 level SIBLING
[   21.793163]   groups: 5 1
[   21.793165]   domain 1: span 0-7 level MC
[   21.793166]    groups: 1,5 2,6 3,7 0,4
[   21.793169] CPU6 attaching sched-domain:
[   21.793171]  domain 0: span 2,6 level SIBLING
[   21.793172]   groups: 6 2
[   21.793174]   domain 1: span 0-7 level MC
[   21.793175]    groups: 2,6 3,7 0,4 1,5
[   21.793178] CPU7 attaching sched-domain:
[   21.793180]  domain 0: span 3,7 level SIBLING
[   21.793181]   groups: 7 3
[   21.793183]   domain 1: span 0-7 level MC
[   21.793184]    groups: 3,7 0,4 1,5 2,6
[   21.793655] CPU0 attaching NULL sched-domain.
[   21.793657] CPU1 attaching NULL sched-domain.
[   21.793659] CPU2 attaching NULL sched-domain.
[   21.793660] CPU3 attaching NULL sched-domain.
[   21.793661] CPU4 attaching NULL sched-domain.
[   21.793662] CPU5 attaching NULL sched-domain.
[   21.793663] CPU6 attaching NULL sched-domain.
[   21.793664] CPU7 attaching NULL sched-domain.
[   21.833033] CPU0 attaching sched-domain:
[   21.833035]  domain 0: span 0,4 level SIBLING
[   21.833038]   groups: 0 4
[   21.833042]   domain 1: span 0-7 level MC
[   21.833044]    groups: 0,4 1,5 2,6 3,7
[   21.833050] CPU1 attaching sched-domain:
[   21.833052]  domain 0: span 1,5 level SIBLING
[   21.833055]   groups: 1 5
[   21.833058]   domain 1: span 0-7 level MC
[   21.833060]    groups: 1,5 2,6 3,7 0,4
[   21.833066] CPU2 attaching sched-domain:
[   21.833068]  domain 0: span 2,6 level SIBLING
[   21.833070]   groups: 2 6
[   21.833074]   domain 1: span 0-7 level MC
[   21.833076]    groups: 2,6 3,7 0,4 1,5
[   21.833083] CPU3 attaching sched-domain:
[   21.833084]  domain 0: span 3,7 level SIBLING
[   21.833085]   groups: 3 7
[   21.833087]   domain 1: span 0-7 level MC
[   21.833088]    groups: 3,7 0,4 1,5 2,6
[   21.833092] CPU4 attaching sched-domain:
[   21.833093]  domain 0: span 0,4 level SIBLING
[   21.833094]   groups: 4 0
[   21.833096]   domain 1: span 0-7 level MC
[   21.833097]    groups: 0,4 1,5 2,6 3,7
[   21.833100] CPU5 attaching sched-domain:
[   21.833102]  domain 0: span 1,5 level SIBLING
[   21.833103]   groups: 5 1
[   21.833105]   domain 1: span 0-7 level MC
[   21.833106]    groups: 1,5 2,6 3,7 0,4
[   21.833109] CPU6 attaching sched-domain:
[   21.833110]  domain 0: span 2,6 level SIBLING
[   21.833112]   groups: 6 2
[   21.833114]   domain 1: span 0-7 level MC
[   21.833115]    groups: 2,6 3,7 0,4 1,5
[   21.833118] CPU7 attaching sched-domain:
[   21.833119]  domain 0: span 3,7 level SIBLING
[   21.833121]   groups: 7 3
[   21.833123]   domain 1: span 0-7 level MC
[   21.833124]    groups: 3,7 0,4 1,5 2,6
[   22.731529] eth0: no IPv6 routers present
[   66.210273] end_request: I/O error, dev fd0, sector 0
[   78.291083] end_request: I/O error, dev fd0, sector 0
[   87.436523] bttv0: PLL can sleep, using XTAL (28636363).

```

How do I fix this?

---

