---
title: "Lenovo Ideapad z585 Precise Installed wifi OK Dual Boot Win 7 no Sound SOLVED"
date: 2013-08-24
forum: Installation &amp; Upgrades
---

### Post by dzup on 2013-08-24
**Lenovo IdeaPad z585 with Ubuntu Precise 32bits Installed** in dual boot using GRUB along Factory Preset Windows 7 Home Premium.

PROS: Wireless works with some extra work (read below).

COS: Have no sound or video playback using Chrome, Firefox, VLC, Video starts playing but freezes in the first frame, then you have to pkill or killall the proccess (firefox, chrome, VLC), else when you try to play .mp3, .ogg, etc sound file the same behavior happens.

PLEASE ADVICE ME HOWTO GET the sound working in this LENOVO IdeaPad z585 Laptop.

THIS IS HOW i manage to install Ubuntu Precise 32 bits in this LENOVO IdeaPad z585 laptop:

(NOTE: you need to connect a ethernet cable to the computer because ***Ubuntu as is,*** is not going to recognize your Wireless Card)

I manage to install Ubuntu Precise 12.04 32 bits Gnome Desktop in this laptop, here are the steps i take:

01.- I upgrade my BIOS to the newest version.
02.- In BIOS i selct USB Legacy support since am booting from a USB drive with YUMI.
03.- BIOS change from UEFI to Legacy and Legacy as prefer device to boot.
04.- In BIOS change the order of booting to first USB boot then hard-drive, Save Settings and Exit.

05.- Now in Windows 7 64 Home Premiun I backup 3 DVDs with the OEM Image.
06.- Using diskpart i erase the last 2 partitions from my hard-drive, leaving only the 100mb and C: partitions.
07.- Resize my C: partition from 750g to 550g, leaving the rest in unallocated Space for my Linux Ubuntu.
08.- Download YUMI or unetbootin and Linux Precise 32bits and create a bootable USB Drive with that image.
09.- Reboot in USB Drive and install Ubuntu as normal (Along with other Operating Systems).
10.- After install Ubuntu, take off the USB Drive and Reboot in Linux Ubuntu from GRUB in HARD-Drive.
11.- Now in Ubuntu i did a apt-get update and upgrade.
12.- After that i installed the suggested missed drivers, that included the wireless driver.

13.- After this Step you will not longer need the Ethernet Cable Since the wireless is now working, go ahead and disconnect ethernet and connect using wireless if you want.

So far that take care of the installation issue, but now i end up with a working Ubuntu, with Sound Driver not working, Am posting this issue in hope someone knows howto get sound driver working in LENOVO IdeaPad z585, here some Hardware Outputs:

```

$ sudo lspci -v | grep -A7 -i "audio"
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9902
    Subsystem: Lenovo Device 3970
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f0244000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

--
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
    Subsystem: Lenovo Device 397b
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f0240000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel



```

```

$ sudo lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
    Subsystem: Lenovo Device 397b
    Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9900 (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 3970
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 2000 [size=256]
    Memory at f0200000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>

00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9902
    Subsystem: Lenovo Device 3970
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f0244000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:06.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device 1234
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: f0100000-f01fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device 1234
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03) (prog-if 30 [XHCI])
    Subsystem: Lenovo Device 397b
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f0248000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [50] Power Management version 3
    Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [90] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [a0] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Latency Tolerance Reporting
    Kernel driver in use: xhci_hcd

00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device 397b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 40
    I/O ports at 2118 [size=8]
    I/O ports at 2124 [size=4]
    I/O ports at 2110 [size=8]
    I/O ports at 2120 [size=4]
    I/O ports at 2100 [size=16]
    Memory at f024c000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [50] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Capabilities: [70] SATA HBA v1.0
    Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: Lenovo Device 397b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f024b000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 397b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f024ca00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: Lenovo Device 397b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f024a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 397b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f024c900 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 14)
    Subsystem: Lenovo Device 397b
    Flags: 66MHz, medium devsel
    Kernel modules: i2c-piix4

00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
    Subsystem: Lenovo Device 397b
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f0240000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
    Subsystem: Lenovo Device 397b
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=64

00:14.7 SD Host controller: Advanced Micro Devices [AMD] Hudson SD Flash Controller (prog-if 01)
    Subsystem: Lenovo Device 397b
    Flags: bus master, 66MHz, medium devsel, latency 71, IRQ 16
    Memory at f024c800 (32-bit, non-prefetchable) [size=256]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 0
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 1
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 2
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 3
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 4
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 5
    Flags: fast devsel

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Lenovo Device 3975
    Flags: bus master, fast devsel, latency 0, IRQ 46
    I/O ports at 1000 [size=256]
    Memory at f0004000 (64-bit, prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 78-02-00-00-36-4c-e0-00
    Kernel driver in use: r8169
    Kernel modules: r8169

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Broadcom Corporation Device 0587
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-b9-ff-ff-97-08-ed
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl, bcma, brcmsmac


```[FONT=Verdana]
[/FONT]
```

$ [COLOR=#222222][FONT=Verdana]sudo aplay 
[/FONT][/COLOR]**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

```

$ dmesg


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-52-generic-pae (buildd@batsu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #78-Ubuntu SMP Fri Jul 26 16:43:19 UTC 2013 (Ubuntu 3.2.0-52.78-generic-pae 3.2.48)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bbce7000 (usable)
[    0.000000]  BIOS-e820: 00000000bbce7000 - 00000000beae7000 (reserved)
[    0.000000]  BIOS-e820: 00000000beae7000 - 00000000bece7000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bece7000 - 00000000bede7000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bede7000 - 00000000bedfe000 (usable)
[    0.000000]  BIOS-e820: 00000000bedfe000 - 00000000bf201000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf201000 - 00000000bf800000 (usable)
[    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed80000 - 00000000fed81000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000019f000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: LENOVO IdeaPad Z585/Lenovo          , BIOS 60CN93WW 10/23/2012
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x19f000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000FF800000 mask FFFFFF800000 write-protect
[    0.000000]   3 base 0000FFEF6000 mask FFFFFFFFE000 uncachable
[    0.000000]   4 base 0000FFEF8000 mask FFFFFFFF8000 uncachable
[    0.000000]   5 base 0000FFF00000 mask FFFFFFFC0000 uncachable
[    0.000000]   6 base 0000FED80000 mask 000FFFFFF000 uncachable
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000019f000000 aka 6640M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] mtrr: your BIOS has configured an incorrect mask, fixing it.
[    0.000000] mtrr: your BIOS has configured an incorrect mask, fixing it.
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffa000-2000000
[    0.000000] RAMDISK: 352c2000 - 36959000
[    0.000000] ACPI: RSDP 000f0150 00024 (v02 LENOVO)
[    0.000000] ACPI: XSDT bede6120 0009C (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: FACP bedd1000 0010C (v05 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI Warning: FADT (revision 5) is longer than ACPI 2.0 version, truncating length 268 to 244 (20110623/tbfadt-288)
[    0.000000] ACPI: DSDT bedd3000 11089 (v01 LENOVO      AMD 00001000 INTL 20061109)
[    0.000000] ACPI: FACS becbe000 00040
[    0.000000] ACPI: SLIC bede5000 00176 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: HPET bedd0000 00038 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: APIC bedcf000 0007A (v02 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: MCFG bedce000 0003C (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: SBST bedcd000 00030 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: FPDT bedcc000 00064 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: UEFI bedcb000 0003E (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: UEFI bedca000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: POAT bedc9000 00055 (v03 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: SSDT bedc8000 00B6C (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: SSDT bedc6000 01ECC (v02    AMD     ALIB 00000001 MSFT 04000000)
[    0.000000] ACPI: SSDT bedc5000 00F13 (v01    AMD    SB900 00000001 INTL 20061109)
[    0.000000] ACPI: UEFI bedc4000 002BA (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: DBG2 bedc2000 000A4 (v00 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 5748MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0019f000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bbce7
[    0.000000]     0: 0x000bede7 -> 0x000bedfe
[    0.000000]     0: 0x000bf201 -> 0x000bf800
[    0.000000]     0: 0x00100000 -> 0x0019f000
[    0.000000] On node 0 totalpages: 1421963
[    0.000000] free_area_init_node: node 0, pgdat c18719c0, node_mem_map f1ee2200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 11497 pages used for memmap
[    0.000000]   HighMem zone: 1182230 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538210 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb3000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1408682
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-52-generic-pae root=UUID=a71cccd0-184c-4bd4-b1e0-168d6044b41d ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 27197184 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0019f000)
[    0.000000] Memory: 5573528k/6799360k available (5837k kernel code, 114324k reserved, 2863k data, 744k init, 4774908k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1880000 - 0xc193a000   ( 744 kB)
[    0.000000]       .data : 0xc15b343c - 0xc187f1c0   (2863 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15b343c   (5837 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2295.464 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4590.92 BogoMIPS (lpj=9181856)
[    0.004005] pid_max: default: 32768 minimum: 301
[    0.004023] Security Framework initialized
[    0.004034] AppArmor: AppArmor initialized
[    0.004036] Yama: becoming mindful.
[    0.004075] Mount-cache hash table entries: 512
[    0.004167] Initializing cgroup subsys cpuacct
[    0.004172] Initializing cgroup subsys memory
[    0.004178] Initializing cgroup subsys devices
[    0.004179] Initializing cgroup subsys freezer
[    0.004181] Initializing cgroup subsys blkio
[    0.004186] Initializing cgroup subsys perf_event
[    0.004203] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.004206] CPU: Physical Processor ID: 0
[    0.004207] CPU: Processor Core ID: 0
[    0.004210] mce: CPU supports 7 MCE banks
[    0.009723] ACPI: Core revision 20110623
[    0.020011] ftrace: allocating 26134 entries in 52 pages
[    0.024051] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024417] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067795] CPU0: AMD A10-4600M APU with Radeon(tm) HD Graphics   stepping 01
[    0.068003] Performance Events: AMD Family 15h PMU driver.
[    0.068003] ... version:                0
[    0.068003] ... bit width:              48
[    0.068003] ... generic registers:      6
[    0.068003] ... value mask:             0000ffffffffffff
[    0.068003] ... max period:             00007fffffffffff
[    0.068003] ... fixed-purpose events:   0
[    0.068003] ... event mask:             000000000000003f
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] CPU 1 irqstacks, hard=f74f0000 soft=f74f2000
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 9a000
[    0.008000] Initializing CPU#1
[    0.008000] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.156029] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156109] CPU 2 irqstacks, hard=f74fe000 soft=f7500000
[    0.156110]  #2
[    0.156112] smpboot cpu 2: start_ip = 9a000
[    0.008000] Initializing CPU#2
[    0.008000] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.248030] NMI watchdog enabled, takes one hw-pmu counter.
[    0.248105] CPU 3 irqstacks, hard=f7514000 soft=f7516000
[    0.248107]  #3 Ok.
[    0.248108] smpboot cpu 3: start_ip = 9a000
[    0.008000] Initializing CPU#3
[    0.008000] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.340034] NMI watchdog enabled, takes one hw-pmu counter.
[    0.340055] Brought up 4 CPUs
[    0.340057] Total of 4 processors activated (18364.64 BogoMIPS).
[    0.340961] devtmpfs: initialized
[    0.340961] EVM: security.selinux
[    0.340961] EVM: security.SMACK64
[    0.340961] EVM: security.capability
[    0.340961] PM: Registering ACPI NVS region at beae7000 (2097152 bytes)
[    0.341034] print_constraints: dummy: 
[    0.341075] RTC time: 15:55:35, date: 08/24/13
[    0.341104] NET: Registered protocol family 16
[    0.341231] EISA bus registered
[    0.341324] Extended Config Space enabled on 0 nodes
[    0.342392] Trying to unpack rootfs image as initramfs...
[    0.341350] ACPI: bus type pci registered
[    0.341435] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.341439] PCI: not using MMCONFIG
[    0.341507] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.341511] PCI: PCI BIOS revision 3.00 entry at 0xfc030, last bus=2
[    0.341513] PCI: Using configuration type 1 for base access
[    0.341514] PCI: Using configuration type 1 for extended access
[    0.344047] bio: create slab <bio-0> at 0
[    0.344084] ACPI: Added _OSI(Module Device)
[    0.344084] ACPI: Added _OSI(Processor Device)
[    0.344084] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.344084] ACPI: Added _OSI(Processor Aggregator Device)
[    0.346865] ACPI: EC: Look up EC in DSDT
[    0.382153] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.564194] ACPI: Interpreter enabled
[    0.564201] ACPI: (supports S0 S3 S4 S5)
[    0.564225] ACPI: Using IOAPIC for interrupt routing
[    0.564379] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.564698] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in ACPI motherboard resources
[    0.564700] PCI: Using MMCONFIG for extended config space
[    0.565161] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.565340] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.569416] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.568366] ACPI: Power Resource [P0L0] (off)
[    0.568412] ACPI: Power Resource [P0L1] (off)
[    0.568457] ACPI: Power Resource [P0L2] (off)
[    0.568502] ACPI: Power Resource [P0L3] (off)
[    0.568960] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.572113] ACPI: No dock devices found.
[    0.572115] HEST: Table not found.
[    0.572119] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.572689] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.573571] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.573574] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c1fff]
[    0.573577] pci_root PNP0A08:00: host bridge window [mem 0x000c2000-0x000c3fff]
[    0.573579] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c5fff]
[    0.573582] pci_root PNP0A08:00: host bridge window [mem 0x000c6000-0x000c7fff]
[    0.573584] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000c9fff]
[    0.573587] pci_root PNP0A08:00: host bridge window [mem 0x000ca000-0x000cbfff]
[    0.573589] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cdfff]
[    0.573591] pci_root PNP0A08:00: host bridge window [mem 0x000ce000-0x000cffff]
[    0.573593] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d1fff]
[    0.573596] pci_root PNP0A08:00: host bridge window [mem 0x000d2000-0x000d3fff]
[    0.573598] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d5fff]
[    0.573600] pci_root PNP0A08:00: host bridge window [mem 0x000d6000-0x000d7fff]
[    0.573603] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000d9fff]
[    0.573605] pci_root PNP0A08:00: host bridge window [mem 0x000da000-0x000dbfff]
[    0.573607] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000ddfff]
[    0.573610] pci_root PNP0A08:00: host bridge window [mem 0x000de000-0x000dffff]
[    0.573612] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e1fff]
[    0.573614] pci_root PNP0A08:00: host bridge window [mem 0x000e2000-0x000e3fff]
[    0.573616] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e5fff]
[    0.573619] pci_root PNP0A08:00: host bridge window [mem 0x000e6000-0x000e7fff]
[    0.573621] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000e9fff]
[    0.573623] pci_root PNP0A08:00: host bridge window [mem 0x000ea000-0x000ebfff]
[    0.573626] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000edfff]
[    0.573628] pci_root PNP0A08:00: host bridge window [mem 0x000ee000-0x000effff]
[    0.573630] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xf7ffffff]
[    0.573633] pci_root PNP0A08:00: host bridge window [mem 0xfc000000-0xfdffffff]
[    0.573635] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    0.573638] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.573640] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.573652] pci_root PNP0A08:00: ignoring host bridge window [mem 0x000ce000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cf9ff])
[    0.573665] pci 0000:00:00.0: [1022:1410] type 0 class 0x000600
[    0.573722] pci 0000:00:01.0: [1002:9900] type 0 class 0x000300
[    0.573730] pci 0000:00:01.0: reg 10: [mem 0xe0000000-0xefffffff pref]
[    0.573736] pci 0000:00:01.0: reg 14: [io  0x2000-0x20ff]
[    0.573742] pci 0000:00:01.0: reg 18: [mem 0xf0200000-0xf023ffff]
[    0.573780] pci 0000:00:01.0: supports D1 D2
[    0.573795] pci 0000:00:01.1: [1002:9902] type 0 class 0x000403
[    0.573804] pci 0000:00:01.1: reg 10: [mem 0xf0244000-0xf0247fff]
[    0.573848] pci 0000:00:01.1: supports D1 D2
[    0.573886] pci 0000:00:06.0: [1022:1416] type 1 class 0x000604
[    0.573932] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.573936] pci 0000:00:06.0: PME# disabled
[    0.573952] pci 0000:00:07.0: [1022:1417] type 1 class 0x000604
[    0.573997] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.574001] pci 0000:00:07.0: PME# disabled
[    0.574055] pci 0000:00:10.0: [1022:7812] type 0 class 0x000c03
[    0.574077] pci 0000:00:10.0: reg 10: [mem 0xf0248000-0xf0249fff 64bit]
[    0.574183] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
[    0.574188] pci 0000:00:10.0: PME# disabled
[    0.574226] pci 0000:00:11.0: [1022:7804] type 0 class 0x000106
[    0.574245] pci 0000:00:11.0: reg 10: [io  0x2118-0x211f]
[    0.574255] pci 0000:00:11.0: reg 14: [io  0x2124-0x2127]
[    0.574265] pci 0000:00:11.0: reg 18: [io  0x2110-0x2117]
[    0.574275] pci 0000:00:11.0: reg 1c: [io  0x2120-0x2123]
[    0.574285] pci 0000:00:11.0: reg 20: [io  0x2100-0x210f]
[    0.574295] pci 0000:00:11.0: reg 24: [mem 0xf024c000-0xf024c7ff]
[    0.574354] pci 0000:00:12.0: [1022:7807] type 0 class 0x000c03
[    0.574368] pci 0000:00:12.0: reg 10: [mem 0xf024b000-0xf024bfff]
[    0.574440] pci 0000:00:12.2: [1022:7808] type 0 class 0x000c03
[    0.574459] pci 0000:00:12.2: reg 10: [mem 0xf024ca00-0xf024caff]
[    0.574542] pci 0000:00:12.2: supports D1 D2
[    0.574544] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.574548] pci 0000:00:12.2: PME# disabled
[    0.574569] pci 0000:00:13.0: [1022:7807] type 0 class 0x000c03
[    0.574583] pci 0000:00:13.0: reg 10: [mem 0xf024a000-0xf024afff]
[    0.574655] pci 0000:00:13.2: [1022:7808] type 0 class 0x000c03
[    0.574674] pci 0000:00:13.2: reg 10: [mem 0xf024c900-0xf024c9ff]
[    0.574757] pci 0000:00:13.2: supports D1 D2
[    0.574759] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.574763] pci 0000:00:13.2: PME# disabled
[    0.574785] pci 0000:00:14.0: [1022:780b] type 0 class 0x000c05
[    0.574862] pci 0000:00:14.2: [1022:780d] type 0 class 0x000403
[    0.574884] pci 0000:00:14.2: reg 10: [mem 0xf0240000-0xf0243fff 64bit]
[    0.574950] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.574954] pci 0000:00:14.2: PME# disabled
[    0.574969] pci 0000:00:14.3: [1022:780e] type 0 class 0x000601
[    0.575045] pci 0000:00:14.4: [1022:780f] type 1 class 0x000604
[    0.575090] pci 0000:00:14.7: [1022:7806] type 0 class 0x000805
[    0.575104] pci 0000:00:14.7: reg 10: [mem 0xf024c800-0xf024c8ff]
[    0.575170] pci 0000:00:18.0: [1022:1400] type 0 class 0x000600
[    0.575191] pci 0000:00:18.1: [1022:1401] type 0 class 0x000600
[    0.575209] pci 0000:00:18.2: [1022:1402] type 0 class 0x000600
[    0.575229] pci 0000:00:18.3: [1022:1403] type 0 class 0x000600
[    0.575253] pci 0000:00:18.4: [1022:1404] type 0 class 0x000600
[    0.575271] pci 0000:00:18.5: [1022:1405] type 0 class 0x000600
[    0.575401] pci 0000:01:00.0: [10ec:8136] type 0 class 0x000200
[    0.575451] pci 0000:01:00.0: reg 10: [io  0x1000-0x10ff]
[    0.575542] pci 0000:01:00.0: reg 18: [mem 0xf0004000-0xf0004fff 64bit pref]
[    0.575597] pci 0000:01:00.0: reg 20: [mem 0xf0000000-0xf0003fff 64bit pref]
[    0.575848] pci 0000:01:00.0: supports D1 D2
[    0.575850] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.575858] pci 0000:01:00.0: PME# disabled
[    0.580105] pci 0000:00:06.0: PCI bridge to [bus 01-01]
[    0.580113] pci 0000:00:06.0:   bridge window [io  0x1000-0x1fff]
[    0.580120] pci 0000:00:06.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.580218] pci 0000:02:00.0: [14e4:4727] type 0 class 0x000280
[    0.580241] pci 0000:02:00.0: reg 10: [mem 0xf0100000-0xf0103fff 64bit]
[    0.580346] pci 0000:02:00.0: supports D1 D2
[    0.580348] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.580353] pci 0000:02:00.0: PME# disabled
[    0.588124] pci 0000:00:07.0: PCI bridge to [bus 02-02]
[    0.588133] pci 0000:00:07.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.588218] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.588228] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.588231] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c1fff] (subtractive decode)
[    0.588233] pci 0000:00:14.4:   bridge window [mem 0x000c2000-0x000c3fff] (subtractive decode)
[    0.588236] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c5fff] (subtractive decode)
[    0.588239] pci 0000:00:14.4:   bridge window [mem 0x000c6000-0x000c7fff] (subtractive decode)
[    0.588241] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000c9fff] (subtractive decode)
[    0.588244] pci 0000:00:14.4:   bridge window [mem 0x000ca000-0x000cbfff] (subtractive decode)
[    0.588246] pci 0000:00:14.4:   bridge window [mem 0x000cc000-0x000cdfff] (subtractive decode)
[    0.588249] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d1fff] (subtractive decode)
[    0.588251] pci 0000:00:14.4:   bridge window [mem 0x000d2000-0x000d3fff] (subtractive decode)
[    0.588254] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d5fff] (subtractive decode)
[    0.588256] pci 0000:00:14.4:   bridge window [mem 0x000d6000-0x000d7fff] (subtractive decode)
[    0.588259] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000d9fff] (subtractive decode)
[    0.588261] pci 0000:00:14.4:   bridge window [mem 0x000da000-0x000dbfff] (subtractive decode)
[    0.588264] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000ddfff] (subtractive decode)
[    0.588266] pci 0000:00:14.4:   bridge window [mem 0x000de000-0x000dffff] (subtractive decode)
[    0.588269] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e1fff] (subtractive decode)
[    0.588271] pci 0000:00:14.4:   bridge window [mem 0x000e2000-0x000e3fff] (subtractive decode)
[    0.588274] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e5fff] (subtractive decode)
[    0.588276] pci 0000:00:14.4:   bridge window [mem 0x000e6000-0x000e7fff] (subtractive decode)
[    0.588279] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000e9fff] (subtractive decode)
[    0.588281] pci 0000:00:14.4:   bridge window [mem 0x000ea000-0x000ebfff] (subtractive decode)
[    0.588283] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000edfff] (subtractive decode)
[    0.588286] pci 0000:00:14.4:   bridge window [mem 0x000ee000-0x000effff] (subtractive decode)
[    0.588288] pci 0000:00:14.4:   bridge window [mem 0xe0000000-0xf7ffffff] (subtractive decode)
[    0.588291] pci 0000:00:14.4:   bridge window [mem 0xfc000000-0xfdffffff] (subtractive decode)
[    0.588293] pci 0000:00:14.4:   bridge window [mem 0xfed40000-0xfed44fff] (subtractive decode)
[    0.588296] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.588298] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.588327] pci_bus 0000:00: on NUMA node 0
[    0.588334] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.588627] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.588672] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[    0.588759] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.588944]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.589235]  pci0000:00: ACPI _OSC control (0x19) granted
[    0.595041] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0
[    0.595099] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0
[    0.595162] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0
[    0.595224] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0
[    0.595272] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0
[    0.595309] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0
[    0.595347] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0
[    0.595385] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0
[    0.595486] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.595486] vgaarb: loaded
[    0.595486] vgaarb: bridge control possible 0000:00:01.0
[    0.595486] i2c-core: driver [aat2870] using legacy suspend method
[    0.595486] i2c-core: driver [aat2870] using legacy resume method
[    0.595486] SCSI subsystem initialized
[    0.595634] libata version 3.00 loaded.
[    0.595634] usbcore: registered new interface driver usbfs
[    0.595634] usbcore: registered new interface driver hub
[    0.595634] usbcore: registered new device driver usb
[    0.595634] PCI: Using ACPI for IRQ routing
[    0.595634] PCI: pci_cache_line_size set to 64 bytes
[    0.596128] reserve RAM buffer: 000000000009e000 - 000000000009ffff 
[    0.596131] reserve RAM buffer: 00000000bbce7000 - 00000000bbffffff 
[    0.596133] reserve RAM buffer: 00000000bedfe000 - 00000000bfffffff 
[    0.596136] reserve RAM buffer: 00000000bf800000 - 00000000bfffffff 
[    0.596138] reserve RAM buffer: 000000019f000000 - 000000019fffffff 
[    0.596235] NetLabel: Initializing
[    0.596237] NetLabel:  domain hash size = 128
[    0.596239] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.596249] NetLabel:  unlabeled traffic allowed by default
[    0.596269] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.596269] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.598119] Switching to clocksource hpet
[    0.603346] AppArmor: AppArmor Filesystem Enabled
[    0.603372] pnp: PnP ACPI init
[    0.603389] ACPI: bus type pnp registered
[    0.603874] pnp 00:00: [bus 00-ff]
[    0.603877] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.603880] pnp 00:00: [mem 0x000c0000-0x000c1fff window]
[    0.603882] pnp 00:00: [mem 0x000c2000-0x000c3fff window]
[    0.603884] pnp 00:00: [mem 0x000c4000-0x000c5fff window]
[    0.603889] pnp 00:00: [mem 0x000c6000-0x000c7fff window]
[    0.603891] pnp 00:00: [mem 0x000c8000-0x000c9fff window]
[    0.603893] pnp 00:00: [mem 0x000ca000-0x000cbfff window]
[    0.603895] pnp 00:00: [mem 0x000cc000-0x000cdfff window]
[    0.603897] pnp 00:00: [mem 0x000ce000-0x000cffff window]
[    0.603899] pnp 00:00: [mem 0x000d0000-0x000d1fff window]
[    0.603902] pnp 00:00: [mem 0x000d2000-0x000d3fff window]
[    0.603904] pnp 00:00: [mem 0x000d4000-0x000d5fff window]
[    0.603906] pnp 00:00: [mem 0x000d6000-0x000d7fff window]
[    0.603908] pnp 00:00: [mem 0x000d8000-0x000d9fff window]
[    0.603910] pnp 00:00: [mem 0x000da000-0x000dbfff window]
[    0.603912] pnp 00:00: [mem 0x000dc000-0x000ddfff window]
[    0.603914] pnp 00:00: [mem 0x000de000-0x000dffff window]
[    0.603916] pnp 00:00: [mem 0x000e0000-0x000e1fff window]
[    0.603918] pnp 00:00: [mem 0x000e2000-0x000e3fff window]
[    0.603921] pnp 00:00: [mem 0x000e4000-0x000e5fff window]
[    0.603923] pnp 00:00: [mem 0x000e6000-0x000e7fff window]
[    0.603925] pnp 00:00: [mem 0x000e8000-0x000e9fff window]
[    0.603927] pnp 00:00: [mem 0x000ea000-0x000ebfff window]
[    0.603929] pnp 00:00: [mem 0x000ec000-0x000edfff window]
[    0.603931] pnp 00:00: [mem 0x000ee000-0x000effff window]
[    0.603933] pnp 00:00: [mem 0xe0000000-0xf7ffffff window]
[    0.603936] pnp 00:00: [mem 0xfc000000-0xfdffffff window]
[    0.603938] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.603940] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.603943] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.603945] pnp 00:00: [io  0x0d00-0xffff window]
[    0.604051] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.604100] pnp 00:01: [io  0x0f50-0x0f51]
[    0.604102] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.604104] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.604107] pnp 00:01: [mem 0xf8000000-0xfbffffff]
[    0.604158] system 00:01: [io  0x0f50-0x0f51] has been reserved
[    0.604162] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.604165] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.604168] system 00:01: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.604172] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.604549] pnp 00:02: [io  0x0000-0x001f]
[    0.604552] pnp 00:02: [io  0x0081-0x008f]
[    0.604554] pnp 00:02: [io  0x00c0-0x00de]
[    0.604556] pnp 00:02: [io  0x040b]
[    0.604557] pnp 00:02: [io  0x04d6]
[    0.604560] pnp 00:02: [dma 4]
[    0.604603] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.604612] pnp 00:03: [io  0x00f0-0x00fe]
[    0.604637] pnp 00:03: [irq 13]
[    0.604682] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.604691] pnp 00:04: [io  0x0070-0x0071]
[    0.604704] pnp 00:04: [irq 8]
[    0.604747] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.604755] pnp 00:05: [io  0x0061]
[    0.604797] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.604818] pnp 00:06: [io  0x0060]
[    0.604820] pnp 00:06: [io  0x0064]
[    0.604840] pnp 00:06: [irq 1]
[    0.604885] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.604984] pnp 00:07: [irq 12]
[    0.605034] pnp 00:07: Plug and Play ACPI device, IDs SYN104d SYN1000 SYN0002 PNP0f13 (active)
[    0.605048] pnp 00:08: [io  0x0022-0x0023]
[    0.605050] pnp 00:08: [io  0x002e-0x002f]
[    0.605052] pnp 00:08: [io  0x0072-0x0073]
[    0.605054] pnp 00:08: [io  0x0080]
[    0.605055] pnp 00:08: [io  0x0092]
[    0.605057] pnp 00:08: [io  0x00b0-0x00b1]
[    0.605059] pnp 00:08: [io  0x00b2]
[    0.605060] pnp 00:08: [io  0x00b8]
[    0.605062] pnp 00:08: [io  0x00bc]
[    0.605064] pnp 00:08: [io  0x00f0]
[    0.605065] pnp 00:08: [io  0x04d0-0x04d1]
[    0.605067] pnp 00:08: [io  0x0530-0x0537]
[    0.605069] pnp 00:08: [io  0x0800-0x0827]
[    0.605071] pnp 00:08: [io  0x0830]
[    0.605072] pnp 00:08: [io  0x0840-0x0847]
[    0.605076] pnp 00:08: [io  0x0b00-0x0b1f]
[    0.605078] pnp 00:08: [io  0x0b20-0x0b3f]
[    0.605080] pnp 00:08: [io  0x0c00-0x0c01]
[    0.605081] pnp 00:08: [io  0x0c14]
[    0.605083] pnp 00:08: [io  0x0c50-0x0c52]
[    0.605085] pnp 00:08: [io  0x0cd0-0x0cd1]
[    0.605087] pnp 00:08: [io  0x0cd2-0x0cd3]
[    0.605088] pnp 00:08: [io  0x0cd4-0x0cd5]
[    0.605090] pnp 00:08: [io  0x0cd6-0x0cd7]
[    0.605092] pnp 00:08: [io  0x0cd8-0x0cdf]
[    0.605094] pnp 00:08: [io  0x0cf9]
[    0.605096] pnp 00:08: [io  0x8100-0x81ff window]
[    0.605098] pnp 00:08: [io  0x8200-0x82ff window]
[    0.605175] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.605177] system 00:08: [io  0x0530-0x0537] has been reserved
[    0.605180] system 00:08: [io  0x0800-0x0827] has been reserved
[    0.605183] system 00:08: [io  0x0830] has been reserved
[    0.605185] system 00:08: [io  0x0840-0x0847] has been reserved
[    0.605188] system 00:08: [io  0x0b00-0x0b1f] has been reserved
[    0.605190] system 00:08: [io  0x0b20-0x0b3f] has been reserved
[    0.605193] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.605195] system 00:08: [io  0x0c14] has been reserved
[    0.605197] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.605200] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
[    0.605202] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
[    0.605205] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.605207] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.605210] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.605212] system 00:08: [io  0x0cf9] could not be reserved
[    0.605215] system 00:08: [io  0x8100-0x81ff window] has been reserved
[    0.605218] system 00:08: [io  0x8200-0x82ff window] has been reserved
[    0.605221] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.605287] pnp 00:09: [mem 0x000e0000-0x000fffff]
[    0.605290] pnp 00:09: [mem 0xffe00000-0xffffffff]
[    0.605292] pnp 00:09: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.605294] pnp 00:09: [mem 0xfec10000-0xfec1001f]
[    0.605296] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.605298] pnp 00:09: [mem 0xfed61000-0xfed613ff]
[    0.605300] pnp 00:09: [mem 0xfed80000-0xfed80fff]
[    0.605324] pnp 00:09: [Firmware Bug]: [mem 0x00000000-0xffffffffffffffff disabled] covers only part of AMD MMCONFIG area [mem 0xf8000000-0xfbffffff]; adding more reservations
[    0.605372] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.605375] system 00:09: [mem 0xffe00000-0xffffffff] has been reserved
[    0.605378] system 00:09: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.605380] system 00:09: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.605383] system 00:09: [mem 0xfed61000-0xfed613ff] has been reserved
[    0.605386] system 00:09: [mem 0xfed80000-0xfed80fff] has been reserved
[    0.605389] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.605732] pnp: PnP ACPI: found 10 devices
[    0.605734] ACPI: ACPI bus type pnp unregistered
[    0.605737] PnPBIOS: Disabled by ACPI PNP
[    0.643467] PCI: max bus depth: 1 pci_try_num: 2
[    0.643486] pci 0000:00:06.0: PCI bridge to [bus 01-01]
[    0.643489] pci 0000:00:06.0:   bridge window [io  0x1000-0x1fff]
[    0.643495] pci 0000:00:06.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.643499] pci 0000:00:07.0: PCI bridge to [bus 02-02]
[    0.643503] pci 0000:00:07.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.643509] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.643532] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.643536] pci 0000:00:06.0: setting latency timer to 64
[    0.643545] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.643548] pci 0000:00:07.0: setting latency timer to 64
[    0.643556] pci_bus 0000:00: resource 4 [mem 0x000a0000-0x000bffff]
[    0.643559] pci_bus 0000:00: resource 5 [mem 0x000c0000-0x000c1fff]
[    0.643561] pci_bus 0000:00: resource 6 [mem 0x000c2000-0x000c3fff]
[    0.643564] pci_bus 0000:00: resource 7 [mem 0x000c4000-0x000c5fff]
[    0.643566] pci_bus 0000:00: resource 8 [mem 0x000c6000-0x000c7fff]
[    0.643568] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000c9fff]
[    0.643571] pci_bus 0000:00: resource 10 [mem 0x000ca000-0x000cbfff]
[    0.643573] pci_bus 0000:00: resource 11 [mem 0x000cc000-0x000cdfff]
[    0.643575] pci_bus 0000:00: resource 12 [mem 0x000d0000-0x000d1fff]
[    0.643578] pci_bus 0000:00: resource 13 [mem 0x000d2000-0x000d3fff]
[    0.643580] pci_bus 0000:00: resource 14 [mem 0x000d4000-0x000d5fff]
[    0.643582] pci_bus 0000:00: resource 15 [mem 0x000d6000-0x000d7fff]
[    0.643584] pci_bus 0000:00: resource 16 [mem 0x000d8000-0x000d9fff]
[    0.643587] pci_bus 0000:00: resource 17 [mem 0x000da000-0x000dbfff]
[    0.643589] pci_bus 0000:00: resource 18 [mem 0x000dc000-0x000ddfff]
[    0.643591] pci_bus 0000:00: resource 19 [mem 0x000de000-0x000dffff]
[    0.643594] pci_bus 0000:00: resource 20 [mem 0x000e0000-0x000e1fff]
[    0.643596] pci_bus 0000:00: resource 21 [mem 0x000e2000-0x000e3fff]
[    0.643598] pci_bus 0000:00: resource 22 [mem 0x000e4000-0x000e5fff]
[    0.643601] pci_bus 0000:00: resource 23 [mem 0x000e6000-0x000e7fff]
[    0.643603] pci_bus 0000:00: resource 24 [mem 0x000e8000-0x000e9fff]
[    0.643605] pci_bus 0000:00: resource 25 [mem 0x000ea000-0x000ebfff]
[    0.643607] pci_bus 0000:00: resource 26 [mem 0x000ec000-0x000edfff]
[    0.643610] pci_bus 0000:00: resource 27 [mem 0x000ee000-0x000effff]
[    0.643612] pci_bus 0000:00: resource 28 [mem 0xe0000000-0xf7ffffff]
[    0.643614] pci_bus 0000:00: resource 29 [mem 0xfc000000-0xfdffffff]
[    0.643617] pci_bus 0000:00: resource 30 [mem 0xfed40000-0xfed44fff]
[    0.643619] pci_bus 0000:00: resource 31 [io  0x0000-0x0cf7]
[    0.643621] pci_bus 0000:00: resource 32 [io  0x0d00-0xffff]
[    0.643624] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.643626] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.643629] pci_bus 0000:02: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.643632] pci_bus 0000:03: resource 4 [mem 0x000a0000-0x000bffff]
[    0.643634] pci_bus 0000:03: resource 5 [mem 0x000c0000-0x000c1fff]
[    0.643636] pci_bus 0000:03: resource 6 [mem 0x000c2000-0x000c3fff]
[    0.643639] pci_bus 0000:03: resource 7 [mem 0x000c4000-0x000c5fff]
[    0.643641] pci_bus 0000:03: resource 8 [mem 0x000c6000-0x000c7fff]
[    0.643643] pci_bus 0000:03: resource 9 [mem 0x000c8000-0x000c9fff]
[    0.643645] pci_bus 0000:03: resource 10 [mem 0x000ca000-0x000cbfff]
[    0.643648] pci_bus 0000:03: resource 11 [mem 0x000cc000-0x000cdfff]
[    0.643650] pci_bus 0000:03: resource 12 [mem 0x000d0000-0x000d1fff]
[    0.643652] pci_bus 0000:03: resource 13 [mem 0x000d2000-0x000d3fff]
[    0.643654] pci_bus 0000:03: resource 14 [mem 0x000d4000-0x000d5fff]
[    0.643657] pci_bus 0000:03: resource 15 [mem 0x000d6000-0x000d7fff]
[    0.643659] pci_bus 0000:03: resource 16 [mem 0x000d8000-0x000d9fff]
[    0.643661] pci_bus 0000:03: resource 17 [mem 0x000da000-0x000dbfff]
[    0.643663] pci_bus 0000:03: resource 18 [mem 0x000dc000-0x000ddfff]
[    0.643665] pci_bus 0000:03: resource 19 [mem 0x000de000-0x000dffff]
[    0.643668] pci_bus 0000:03: resource 20 [mem 0x000e0000-0x000e1fff]
[    0.643670] pci_bus 0000:03: resource 21 [mem 0x000e2000-0x000e3fff]
[    0.643672] pci_bus 0000:03: resource 22 [mem 0x000e4000-0x000e5fff]
[    0.643674] pci_bus 0000:03: resource 23 [mem 0x000e6000-0x000e7fff]
[    0.643677] pci_bus 0000:03: resource 24 [mem 0x000e8000-0x000e9fff]
[    0.643679] pci_bus 0000:03: resource 25 [mem 0x000ea000-0x000ebfff]
[    0.643681] pci_bus 0000:03: resource 26 [mem 0x000ec000-0x000edfff]
[    0.643683] pci_bus 0000:03: resource 27 [mem 0x000ee000-0x000effff]
[    0.643686] pci_bus 0000:03: resource 28 [mem 0xe0000000-0xf7ffffff]
[    0.643688] pci_bus 0000:03: resource 29 [mem 0xfc000000-0xfdffffff]
[    0.643690] pci_bus 0000:03: resource 30 [mem 0xfed40000-0xfed44fff]
[    0.643693] pci_bus 0000:03: resource 31 [io  0x0000-0x0cf7]
[    0.643695] pci_bus 0000:03: resource 32 [io  0x0d00-0xffff]
[    0.643731] NET: Registered protocol family 2
[    0.643791] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.643989] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.644295] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.644428] TCP: Hash tables configured (established 131072 bind 65536)
[    0.644430] TCP reno registered
[    0.644433] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.644440] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.644501] NET: Registered protocol family 1
[    0.644515] pci 0000:00:01.0: Boot video device
[    0.644545] pci 0000:00:10.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.644578] pci 0000:00:10.0: PCI INT A disabled
[    0.644588] pci 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.716137] pci 0000:00:12.0: PCI INT A disabled
[    0.716164] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.716186] pci 0000:00:12.2: PCI INT B disabled
[    0.716194] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.727181] Freeing initrd memory: 23132k freed
[    0.788159] pci 0000:00:13.0: PCI INT A disabled
[    0.788175] pci 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.788194] pci 0000:00:13.2: PCI INT B disabled
[    0.788260] PCI: CLS 32 bytes, default 64
[    0.788888] [Firmware Bug]: cpu 1, try to use APIC500 (LVT offset 0) for vector 0x10400, but the register is already in use for vector 0xf9 on another cpu
[    0.788892] [Firmware Bug]: cpu 1, IBS interrupt offset 0 not available (MSRC001103A=0x0000000000000100)
[    0.788894] Failed to setup IBS, -22
[    0.789182] audit: initializing netlink socket (disabled)
[    0.789198] type=2000 audit(1377359734.788:1): initialized
[    0.809511] highmem bounce pool size: 64 pages
[    0.809515] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.812115] VFS: Disk quotas dquot_6.5.2
[    0.812177] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.812786] fuse init (API version 7.17)
[    0.812898] msgmni has been set to 1604
[    0.813387] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.813440] io scheduler noop registered
[    0.813443] io scheduler deadline registered
[    0.813451] io scheduler cfq registered (default)
[    0.813633] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.813653] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.993152] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.997616] ACPI: AC Adapter [ACAD] (on-line)
[    0.997745] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.997750] ACPI: Power Button [PWRB]
[    0.997791] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.997795] ACPI: Sleep Button [SLPB]
[    0.998020] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    1.004297] ACPI: Lid Switch [LID]
[    1.004368] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.004373] ACPI: Power Button [PWRF]
[    1.008308] ACPI: Fan [Z0F0] (off)
[    1.012282] ACPI: Fan [Z0F1] (off)
[    1.012329] ACPI: Fan [Z0F2] (off)
[    1.012367] ACPI: Fan [Z0F3] (off)
[    1.012441] ACPI: acpi_idle registered with cpuidle
[    1.018702] thermal LNXTHERM:00: registered as thermal_zone0
[    1.018706] ACPI: Thermal Zone [TZ00] (50 C)
[    1.019166] thermal LNXTHERM:01: registered as thermal_zone1
[    1.019168] ACPI: Thermal Zone [THZ0] (51 C)
[    1.019204] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.019215] ACPI: Battery Slot [BAT1] (battery present)
[    1.019247] ERST: Table is not found!
[    1.019249] GHES: HEST is not enabled!
[    1.019418] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.019503] isapnp: Scanning for PnP cards...
[    1.049971] ACPI: Battery Slot [BAT1] (battery present)
[    1.386501] isapnp: No Plug & Play device found
[    1.390532] Linux agpgart interface v0.103
[    1.392233] brd: module loaded
[    1.393094] loop: module loaded
[    1.393206] ahci 0000:00:11.0: version 3.0
[    1.393233] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.393281] ahci 0000:00:11.0: irq 40 for MSI/MSI-X
[    1.393335] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    1.393338] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.393727] scsi0 : ahci
[    1.393841] scsi1 : ahci
[    1.394085] ata1: SATA max UDMA/133 abar m2048@0xf024c000 port 0xf024c100 irq 40
[    1.394089] ata2: SATA max UDMA/133 abar m2048@0xf024c000 port 0xf024c180 irq 40
[    1.394514] Fixed MDIO Bus: probed
[    1.394535] tun: Universal TUN/TAP device driver, 1.6
[    1.394536] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.394612] PPP generic driver version 2.4.2
[    1.394720] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.394733] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.394745] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.394786] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.394793] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.394813] QUIRK: Enable AMD PLL fix
[    1.394822] ehci_hcd 0000:00:12.2: debug port 1
[    1.394839] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf024ca00
[    1.404149] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.404321] hub 1-0:1.0: USB hub found
[    1.404325] hub 1-0:1.0: 5 ports detected
[    1.404432] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.404453] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.404507] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.404514] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.404532] ehci_hcd 0000:00:13.2: debug port 1
[    1.404544] ehci_hcd 0000:00:13.2: irq 17, io mem 0xf024c900
[    1.416150] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.416314] hub 2-0:1.0: USB hub found
[    1.416318] hub 2-0:1.0: 5 ports detected
[    1.416409] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.416442] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.416463] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.416514] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.416537] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf024b000
[    1.476276] hub 3-0:1.0: USB hub found
[    1.476298] hub 3-0:1.0: 5 ports detected
[    1.476378] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.476399] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.476449] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    1.476464] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf024a000
[    1.536300] hub 4-0:1.0: USB hub found
[    1.536323] hub 4-0:1.0: 5 ports detected
[    1.536388] uhci_hcd: USB Universal Host Controller Interface driver
[    1.536443] xhci_hcd 0000:00:10.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.536465] xhci_hcd 0000:00:10.0: setting latency timer to 64
[    1.536468] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.536522] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 5
[    1.536760] xhci_hcd 0000:00:10.0: irq 41 for MSI/MSI-X
[    1.536766] xhci_hcd 0000:00:10.0: irq 42 for MSI/MSI-X
[    1.536771] xhci_hcd 0000:00:10.0: irq 43 for MSI/MSI-X
[    1.536776] xhci_hcd 0000:00:10.0: irq 44 for MSI/MSI-X
[    1.536781] xhci_hcd 0000:00:10.0: irq 45 for MSI/MSI-X
[    1.536928] xHCI xhci_add_endpoint called for root hub
[    1.536930] xHCI xhci_check_bandwidth called for root hub
[    1.536955] hub 5-0:1.0: USB hub found
[    1.536975] hub 5-0:1.0: 2 ports detected
[    1.537026] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.537083] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
[    1.540190] xHCI xhci_add_endpoint called for root hub
[    1.540191] xHCI xhci_check_bandwidth called for root hub
[    1.540212] hub 6-0:1.0: USB hub found
[    1.540218] hub 6-0:1.0: 2 ports detected
[    1.588217] usbcore: registered new interface driver libusual
[    1.588256] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE3] at 0x60,0x64 irq 1,12
[    1.592524] i8042: Detected active multiplexing controller, rev 1.1
[    1.594000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.594009] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.594036] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.594056] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.594077] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.594219] mousedev: PS/2 mouse device common for all mice
[    1.594449] rtc_cmos 00:04: RTC can wake from S4
[    1.594551] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.594574] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.594623] device-mapper: uevent: version 1.0.3
[    1.594711] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.594728] EISA: Probing bus 0 at eisa.0
[    1.594730] EISA: Cannot allocate resource for mainboard
[    1.594732] Cannot allocate resource for EISA slot 1
[    1.594734] Cannot allocate resource for EISA slot 2
[    1.594735] Cannot allocate resource for EISA slot 3
[    1.594737] Cannot allocate resource for EISA slot 4
[    1.594738] Cannot allocate resource for EISA slot 5
[    1.594739] Cannot allocate resource for EISA slot 6
[    1.594741] Cannot allocate resource for EISA slot 7
[    1.594742] Cannot allocate resource for EISA slot 8
[    1.594744] EISA: Detected 0 cards.
[    1.594768] cpufreq-nforce2: No nForce2 chipset.
[    1.594840] cpuidle: using governor ladder
[    1.595080] cpuidle: using governor menu
[    1.595082] EFI Variables Facility v0.08 2004-May-17
[    1.595321] TCP cubic registered
[    1.595437] NET: Registered protocol family 10
[    1.595962] NET: Registered protocol family 17
[    1.595966] Registering the dns_resolver key type
[    1.595982] Using IPI No-Shortcut mode
[    1.596143] PM: Hibernation image not present or could not be loaded.
[    1.596152] registered taskstats version 1
[    1.604091]   Magic number: 9:298:943
[    1.604123] tty tty0: hash matches
[    1.604125] tty console: hash matches
[    1.604191] rtc_cmos 00:04: setting system clock to 2013-08-24 15:55:36 UTC (1377359736)
[    1.604223] powernow-k8: Found 1 AMD A10-4600M APU with Radeon(tm) HD Graphics   (4 cpu cores) (version 2.20.00)
[    1.604253] powernow-k8: Core Performance Boosting: on.
[    1.604297] powernow-k8:    0 : pstate 0 (2300 MHz)
[    1.604299] powernow-k8:    1 : pstate 1 (2000 MHz)
[    1.604300] powernow-k8:    2 : pstate 2 (1800 MHz)
[    1.604302] powernow-k8:    3 : pstate 3 (1600 MHz)
[    1.604304] powernow-k8:    4 : pstate 4 (1400 MHz)
[    1.604833] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.604835] EDD information not available.
[    1.634894] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.716174] usb 1-3: new high-speed USB device number 2 using ehci_hcd
[    1.788157] Refined TSC clocksource calibration: 2295.709 MHz.
[    1.788165] Switching to clocksource tsc
[    1.888169] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.888195] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.890042] ata2.00: ATAPI: Optiarc DVD RW AD-7740H, A841, max UDMA/100
[    1.892208] ata2.00: configured for UDMA/100
[    1.894820] ata1.00: failed to enable AA (error_mask=0x1)
[    1.894825] ata1.00: ATA-8: ST750LM022 HN-M750MBB, 2AR10001, max UDMA/100
[    1.894828] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.901447] ata1.00: failed to enable AA (error_mask=0x1)
[    1.901455] ata1.00: configured for UDMA/100
[    1.901584] scsi 0:0:0:0: Direct-Access     ATA      ST750LM022 HN-M7 2AR1 PQ: 0 ANSI: 5
[    1.901789] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.901793] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.901797] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.901876] sd 0:0:0:0: [sda] Write Protect is off
[    1.901879] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.901916] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.902362] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7740H  A841 PQ: 0 ANSI: 5
[    1.904661] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.904665] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.904930] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.905015] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.969590]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.970278] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.970382] Freeing unused kernel memory: 744k freed
[    1.970673] Write protecting the kernel text: 5840k
[    1.970699] Write protecting the kernel read-only data: 2388k
[    1.970701] NX-protecting the kernel data: 4400k
[    1.996517] zram: module is from the staging directory, the quality is unknown, you have been warned.
[    1.996855] zram: num_devices not specified. Using default: 1
[    1.996857] zram: Creating 1 devices ...
[    2.001612] udevd[107]: starting version 175
[    2.035117] Adding 2798700k swap on /dev/zram0.  Priority:100 extents:1 across:2798700k SS
[    2.080166] usb 2-3: new high-speed USB device number 2 using ehci_hcd
[    2.258761] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.260435] r8169 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.260462] r8169 0000:01:00.0: setting latency timer to 64
[    2.260513] r8169 0000:01:00.0: irq 46 for MSI/MSI-X
[    2.261176] r8169 0000:01:00.0: eth0: RTL8105e at 0xf8462000, 04:7d:7b:e9:82:1f, XID 00c00000 IRQ 46
[    2.263890] sdhci: Secure Digital Host Controller Interface driver
[    2.263894] sdhci: Copyright(c) Pierre Ossman
[    2.266083] sdhci-pci 0000:00:14.7: SDHCI controller found [1022:7806] (rev 0)
[    2.266110] sdhci-pci 0000:00:14.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.266166] mmc0: no vmmc regulator found
[    2.266209] Registered led device: mmc0::
[    2.267458] mmc0: SDHCI controller on PCI [0000:00:14.7] using ADMA
[    2.276471] wmi: Mapper loaded
[    2.336349] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    2.476159] usb 3-4: new full-speed USB device number 2 using ohci_hcd
[    2.484383] acpi device:40: registered as cooling_device8
[    2.484462] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:02/input/input5
[    2.484739] ACPI: Video Device [VGA2] (multi-head: yes  rom: no  post: no)
[    3.843423] vesafb: mode is 1366x768x32, linelength=5632, pages=0
[    3.843426] vesafb: scrolling: redraw
[    3.843429] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    3.843436] mtrr: your BIOS has configured an incorrect mask, fixing it.
[    3.843440] mtrr: your BIOS has configured an incorrect mask, fixing it.
[    3.844615] vesafb: framebuffer at 0xe0000000, mapped to 0xf8b00000, using 4224k, total 4224k
[    3.844779] Console: switching to colour frame buffer device 170x48
[    3.844810] fb0: VESA VGA frame buffer device
[    5.127263] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    5.127266] EXT4-fs (sda5): write access will be enabled during recovery
[    6.677367] EXT4-fs (sda5): recovery complete
[    6.687946] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   22.343861] Adding 5686268k swap on /dev/sda6.  Priority:-1 extents:1 across:5686268k 
[   22.351540] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.378615] udevd[398]: starting version 175
[   22.396237] lp: driver loaded but no devices found
[   22.548305] ACPI Error: [SSZE] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
[   22.548314] ACPI Error: Method parse/execution failed [\_SB_.ACAD._PSR] (Node f7439d38), AE_ALREADY_EXISTS (20110623/psparse-536)
[   22.548327] ACPI Exception: AE_ALREADY_EXISTS, Error reading AC Adapter state (20110623/ac-118)
[   22.576036] ACPI: Marking method _PSR as Serialized because of AE_ALREADY_EXISTS error
[   22.586518] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   22.622635] lib80211: common routines for IEEE802.11 drivers
[   22.622640] lib80211_crypt: registered algorithm 'NULL'
[   22.624957] cfg80211: Calling CRDA to update world regulatory domain
[   22.634713] wl: module license 'MIXED/Proprietary' taints kernel.
[   22.634717] Disabling lock debugging due to kernel taint
[   22.656528] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMB0 [io 0xb00-0xb0f]
[   22.656532] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.672411] wl 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   22.672423] wl 0000:02:00.0: setting latency timer to 64
[   22.678875] snd_hda_intel 0000:00:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   22.678932] snd_hda_intel 0000:00:01.1: irq 47 for MSI/MSI-X
[   22.678953] snd_hda_intel 0000:00:01.1: setting latency timer to 64
[   22.701496] Linux video capture interface: v2.00
[   22.702471] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (5986:0295)
[   22.707395] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input6
[   22.707550] usbcore: registered new interface driver uvcvideo
[   22.707553] USB Video Class driver (1.1.1)
[   22.710517] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   22.710521] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710524] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   22.710528] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710531] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   22.710534] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710537] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   22.710541] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710543] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   22.710547] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710550] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   22.710553] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710555] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   22.710559] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710561] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   22.710565] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710567] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   22.710571] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710574] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   22.710577] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710580] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   22.710583] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710586] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   22.710589] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710592] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   22.710596] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710599] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   22.710602] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   22.710605] cfg80211: Disabling freq 5170 MHz
[   22.710608] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   22.710611] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710614] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   22.710617] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710620] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   22.710624] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710626] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[   22.710630] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710633] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   22.710636] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710639] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   22.710642] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710645] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   22.710649] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710651] cfg80211: Disabling freq 5260 MHz
[   22.710653] cfg80211: Disabling freq 5280 MHz
[   22.710655] cfg80211: Disabling freq 5300 MHz
[   22.710657] cfg80211: Disabling freq 5320 MHz
[   22.710659] cfg80211: Disabling freq 5500 MHz
[   22.710661] cfg80211: Disabling freq 5520 MHz
[   22.710662] cfg80211: Disabling freq 5540 MHz
[   22.710664] cfg80211: Disabling freq 5560 MHz
[   22.710666] cfg80211: Disabling freq 5580 MHz
[   22.710668] cfg80211: Disabling freq 5600 MHz
[   22.710670] cfg80211: Disabling freq 5620 MHz
[   22.710672] cfg80211: Disabling freq 5640 MHz
[   22.710674] cfg80211: Disabling freq 5660 MHz
[   22.710676] cfg80211: Disabling freq 5680 MHz
[   22.710677] cfg80211: Disabling freq 5700 MHz
[   22.710679] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   22.710683] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710685] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   22.710689] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710691] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   22.710694] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710697] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   22.710700] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710702] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   22.710705] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.710708] cfg80211: Disabling freq 5920 MHz
[   22.710710] cfg80211: Disabling freq 5940 MHz
[   22.710711] cfg80211: Disabling freq 5960 MHz
[   22.710713] cfg80211: Disabling freq 5980 MHz
[   22.710715] cfg80211: Disabling freq 6000 MHz
[   22.710717] cfg80211: Disabling freq 6020 MHz
[   22.710719] cfg80211: Disabling freq 6040 MHz
[   22.710721] cfg80211: Disabling freq 6060 MHz
[   22.710723] cfg80211: Disabling freq 6080 MHz
[   22.711490] Bluetooth: Core ver 2.16
[   22.711518] NET: Registered protocol family 31
[   22.711521] Bluetooth: HCI device and connection manager initialized
[   22.711524] Bluetooth: HCI socket layer initialized
[   22.711527] Bluetooth: L2CAP socket layer initialized
[   22.711533] Bluetooth: SCO socket layer initialized
[   22.711915] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   22.712597] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   22.713599] usbcore: registered new interface driver btusb
[   22.714261] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   22.715222] Initializing rts5139 USB card reader driver...
[   22.718786] lib80211_crypt: registered algorithm 'TKIP'
[   22.726418] scsi2 : SCSI emulation for RTS5139 USB card reader
[   22.727668] scsi 2:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   22.731751] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   22.735675] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   22.754464] type=1400 audit(1377377757.647:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=634 comm="apparmor_parser"
[   22.754911] type=1400 audit(1377377757.647:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=634 comm="apparmor_parser"
[   22.755171] type=1400 audit(1377377757.647:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=634 comm="apparmor_parser"
[   22.764081] usbcore: registered new interface driver rts5139
[   22.764085] Realtek rts5139 USB card reader support registered.
[   22.818395] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   22.818400] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818403] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   22.818407] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818410] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   22.818414] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818417] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   22.818420] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818423] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   22.818426] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818429] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   22.818433] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818435] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   22.818439] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818442] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   22.818445] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818448] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   22.818451] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818454] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   22.818457] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818460] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   22.818463] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818466] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   22.818470] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.818473] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   22.818476] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.818479] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   22.818482] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.818485] cfg80211: Disabling freq 5170 MHz
[   22.818487] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   22.818491] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818494] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   22.818497] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818500] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   22.818503] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818506] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[   22.818509] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818512] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   22.818515] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818518] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   22.818522] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818524] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   22.818528] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818530] cfg80211: Disabling freq 5260 MHz
[   22.818532] cfg80211: Disabling freq 5280 MHz
[   22.818534] cfg80211: Disabling freq 5300 MHz
[   22.818536] cfg80211: Disabling freq 5320 MHz
[   22.818538] cfg80211: Disabling freq 5500 MHz
[   22.818540] cfg80211: Disabling freq 5520 MHz
[   22.818542] cfg80211: Disabling freq 5540 MHz
[   22.818544] cfg80211: Disabling freq 5560 MHz
[   22.818545] cfg80211: Disabling freq 5580 MHz
[   22.818547] cfg80211: Disabling freq 5600 MHz
[   22.818549] cfg80211: Disabling freq 5620 MHz
[   22.818551] cfg80211: Disabling freq 5640 MHz
[   22.818553] cfg80211: Disabling freq 5660 MHz
[   22.818555] cfg80211: Disabling freq 5680 MHz
[   22.818557] cfg80211: Disabling freq 5700 MHz
[   22.818559] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   22.818562] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818565] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   22.818568] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818571] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   22.818574] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818577] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   22.818580] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818583] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   22.818587] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818589] cfg80211: Disabling freq 5920 MHz
[   22.818592] cfg80211: Disabling freq 5940 MHz
[   22.818593] cfg80211: Disabling freq 5960 MHz
[   22.818596] cfg80211: Disabling freq 5980 MHz
[   22.818598] cfg80211: Disabling freq 6000 MHz
[   22.818599] cfg80211: Disabling freq 6020 MHz
[   22.818601] cfg80211: Disabling freq 6040 MHz
[   22.818603] cfg80211: Disabling freq 6060 MHz
[   22.818605] cfg80211: Disabling freq 6080 MHz
[   22.818609] cfg80211: World regulatory domain updated:
[   22.818611] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.818615] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818618] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.818621] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.818624] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.818627] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.957504] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   22.981261] input: Ideapad extra buttons as /devices/platform/ideapad/input/input7
[   23.049816] init: failsafe main process (820) killed by TERM signal
[   23.162317] Bluetooth: RFCOMM TTY layer initialized
[   23.162324] Bluetooth: RFCOMM socket layer initialized
[   23.162326] Bluetooth: RFCOMM ver 1.11
[   23.175901] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.175905] Bluetooth: BNEP filters: protocol multicast
[   23.189476] type=1400 audit(1377377758.083:5): apparmor="STATUS" operation="profile_load" name="system_tor" pid=911 comm="apparmor_parser"
[   23.191613] type=1400 audit(1377377758.083:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=910 comm="apparmor_parser"
[   23.192148] type=1400 audit(1377377758.087:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=910 comm="apparmor_parser"
[   23.192434] type=1400 audit(1377377758.087:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=910 comm="apparmor_parser"
[   23.195250] type=1400 audit(1377377758.087:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=916 comm="apparmor_parser"
[   23.195816] type=1400 audit(1377377758.087:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=916 comm="apparmor_parser"
[   23.196444] type=1400 audit(1377377758.091:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=909 comm="apparmor_parser"
[   23.203390] Too many HDMI devices
[   23.203394] Too many HDMI devices
[   23.203396] Too many HDMI devices
[   23.203398] Too many HDMI devices
[   23.203400] Too many HDMI devices
[   23.203401] Too many HDMI devices
[   23.203497] hda-codec: out of range cmd 0:0:1c34:707:40
[   23.203500] hda-codec: out of range cmd 0:0:1c34:708:85
[   23.203639] hda-codec: out of range cmd 0:0:1c34:f00:c
[   23.203642] hda-codec: out of range cmd 0:0:1c34:709:0
[   23.203644] hda-codec: out of range cmd 0:0:1c34:f09:0
[   23.203671] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   23.203726] HDMI status: Codec=0 Pin=0 Presence_Detect=0 ELD_Valid=0
[   23.203769] HDMI status: Codec=0 Pin=0 Presence_Detect=0 ELD_Valid=0
[   23.203816] HDMI status: Codec=0 Pin=0 Presence_Detect=0 ELD_Valid=0
[   23.203845] HDMI status: Codec=0 Pin=7220 Presence_Detect=1 ELD_Valid=1
[   23.203847] hda-codec: out of range cmd 0:0:1c34:f2e:8
[   23.203850] hda_codec: cannot build controls for #0 (error -16)
[   23.204566] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.247816] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input8
[   23.247922] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input9
[   23.636582] psmouse serio4: synaptics: Touchpad model: 1, fw: 8.0, id: 0x1e2b1, caps: 0xd00123/0x840300/0x123c00
[   23.681871] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   24.156065] ppdev: user-space parallel port driver
[   24.219385] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.219410] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.219715] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.219745] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.219859] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.219954] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.220180] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.220248] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.220897] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.220922] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.221507] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.221525] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.222050] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.222067] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.222593] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.222610] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.222953] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.222969] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.223507] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.223525] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.224131] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.224158] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.224776] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.224797] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.225372] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.225389] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.225932] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.225948] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.226569] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.226589] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.226988] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.227005] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.227365] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.227382] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.227917] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.227933] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.228595] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.228616] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.229214] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.229231] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.229763] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.229780] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.230327] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.230344] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.230887] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.230903] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.231493] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.231512] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.232188] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.232209] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.232836] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.232856] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.233455] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.233472] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.234022] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.234039] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.234589] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.234606] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.235140] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.235156] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.235718] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.235738] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.236399] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.236420] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.236803] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.236820] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.237226] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.237245] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.237652] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.237672] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.238061] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.238078] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.238443] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.238459] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.238818] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.238835] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.239379] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.239396] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.239942] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.239959] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.240550] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.240568] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.240936] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.240953] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.241305] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.241321] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.241681] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.241698] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.242058] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.242085] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.242490] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.242510] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.242918] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.242937] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.243327] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.243355] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.243759] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.243779] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.244236] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.244257] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.244638] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.244655] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.245009] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.245026] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.245392] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.245409] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.245786] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.245803] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.246160] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.246177] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.246543] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.246560] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.246926] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.246943] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.247491] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.247508] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.248105] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.248127] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.248693] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.248828] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.248866] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.248906] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.250343] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.250705] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.251230] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.251510] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.252064] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.252346] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.252919] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.253239] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.253821] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.254129] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.254520] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.254841] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.255398] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.255668] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.256242] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.256511] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.257052] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.257331] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.257870] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.258139] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.258749] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.259068] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.259649] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.259920] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.260303] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.260575] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.260930] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.261198] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.261735] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.262009] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.262625] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.262943] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.263514] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.263785] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.264341] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.264627] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.265203] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.265522] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.266123] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.266394] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.266971] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.267294] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.267881] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.268253] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.268913] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.269192] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.269767] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.270092] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.270695] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.270963] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.271503] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.271780] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.272341] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.272614] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.273148] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.273415] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.273958] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.274234] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.274606] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.274922] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.275324] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.275634] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.275997] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.276294] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.276648] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.276916] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.277275] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.277540] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.277908] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.278179] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.278725] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.278998] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.279627] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.279944] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.280601] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.280928] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.281339] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.281617] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.281968] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.282233] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.282590] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.282860] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.283218] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.283485] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.283833] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.284127] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.284490] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.284763] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.285125] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.285392] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.285745] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.286013] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.286376] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.286645] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.287007] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.287276] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.287693] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.288026] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.288465] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.288740] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.289103] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.289371] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.289732] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.289996] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.290360] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.290640] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.291005] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.291275] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.291840] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.292196] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.292822] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.293125] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.293746] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.294122] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.294158] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.294919] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.295253] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.295495] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.295516] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.295580] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.298254] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.298319] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.298352] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.298404] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.298424] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.322765] Bluetooth: can't load firmware, may not work correctly
[   24.370248] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.370273] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.449363] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.449402] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.506871] r8169 0000:01:00.0: eth0: link down
[   24.507036] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.507428] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.526681] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.526744] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.526789] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.526821] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.790250] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.790296] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.791683] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.791703] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   24.794014] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   26.158420] postgres (1237): /proc/1237/oom_adj is deprecated, please use /proc/1237/oom_score_adj instead.
[   26.457393] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   26.487575] mtrr: your BIOS has configured an incorrect mask, fixing it.
[   26.986623] BUG: unable to handle kernel NULL pointer dereference at   (null)
[   26.986630] IP: [<  (null)>]   (null)
[   26.986635] *pdpt = 000000002c648001 *pde = 0000000000000000 
[   26.986640] Oops: 0010 [#1] SMP 
[   26.986644] Modules linked in: parport_pc ppdev joydev snd_hda_codec_realtek snd_hda_codec_hdmi bnep rfcomm binfmt_misc lib80211_crypt_tkip rts5139(C) btusb bluetooth uvcvideo videodev snd_seq_midi snd_rawmidi snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi_event k10temp psmouse serio_raw i2c_piix4 snd_seq snd_timer snd_seq_device wl(P) ideapad_laptop snd sparse_keymap soundcore snd_page_alloc cfg80211 lib80211 mac_hid lp parport vesafb sdhci_pci sdhci r8169 wmi video zram(C)
[   26.986691] 
[   26.986695] Pid: 1336, comm: pulseaudio Tainted: P         CIO 3.2.0-52-generic-pae #78-Ubuntu LENOVO IdeaPad Z585/Lenovo          
[   26.986702] EIP: 0060:[<00000000>] EFLAGS: 00210292 CPU: 2
[   26.986706] EIP is at 0x0
[   26.986709] EAX: f75d4e2c EBX: f75a0930 ECX: ecd05800 EDX: ed34dc00
[   26.986712] ESI: ed37fc00 EDI: ed397e4c EBP: ec69bd3c ESP: ec69bd14
[   26.986715]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   26.986718] Process pulseaudio (pid: 1336, ti=ec69a000 task=ec5b32c0 task.ti=ec69a000)
[   26.986721] Stack:
[   26.986723]  f914eb73 00000080 ed2d9e38 f75a0930 f75d4e2c ed2d9e00 ecd05800 ec69bd88
[   26.986731]  00000000 ec5b32c0 ec69bd54 f913ff63 ec69bd48 ecd05800 ed2a8000 00000000
[   26.986739]  ec69bd98 f9140072 ec69bd88 00000040 00000000 ed2a80f4 ec6d9180 ed2a80e0
[   26.986747] Call Trace:
[   26.986755]  [<f914eb73>] ? azx_pcm_open+0x1d3/0x280 [snd_hda_intel]
[   26.986764]  [<f913ff63>] snd_pcm_open_substream+0x53/0x90 [snd_pcm]
[   26.986772]  [<f9140072>] snd_pcm_open+0xd2/0x270 [snd_pcm]
[   26.986778]  [<c10543a0>] ? try_to_wake_up+0x190/0x190
[   26.986786]  [<f907e044>] ? snd_lookup_minor_data+0x44/0x70 [snd]
[   26.986794]  [<f91402c2>] snd_pcm_playback_open+0x42/0x60 [snd_pcm]
[   26.986802]  [<f907e596>] snd_open+0x116/0x270 [snd]
[   26.986808]  [<c1149de6>] chrdev_open+0xb6/0x200
[   26.986813]  [<c1143df6>] __dentry_open+0x276/0x330
[   26.986818]  [<c1149d30>] ? cdev_put+0x20/0x20
[   26.986821]  [<c114437a>] vfs_open+0x3a/0x50
[   26.986825]  [<c11452a9>] nameidata_to_filp+0x39/0x40
[   26.986829]  [<c1152807>] do_last+0x367/0x660
[   26.986833]  [<c1153b34>] path_openat+0xa4/0x350
[   26.986839]  [<c117d8c4>] ? fsnotify_put_event+0x44/0x60
[   26.986843]  [<c117d8c4>] ? fsnotify_put_event+0x44/0x60
[   26.986847]  [<c1153ef1>] do_filp_open+0x31/0x80
[   26.986853]  [<c12b9f88>] ? strncpy_from_user+0x38/0x70
[   26.986857]  [<c115f533>] ? alloc_fd+0xa3/0xe0
[   26.986861]  [<c114539d>] do_sys_open+0xed/0x210
[   26.986869]  [<f90833e0>] ? snd_ctl_elem_add_user+0x70/0x70 [snd]
[   26.986873]  [<c11454ee>] sys_open+0x2e/0x40
[   26.986879]  [<c15b209f>] sysenter_do_call+0x12/0x28
[   26.986881] Code:  Bad EIP value.
[   26.986886] EIP: [<00000000>] 0x0 SS:ESP 0068:ec69bd14
[   26.986892] CR2: 0000000000000000
[   26.986895] ---[ end trace cca289af616fb723 ]---
[   30.640826] init: plymouth-stop pre-start process (1665) terminated with status 1
[   80.224096] eth1: no IPv6 routers present
[ 1021.532088] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 1021.926932] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 1054.124214] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 1054.199031] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 2613.331918] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 2613.336559] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 2636.882813] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 2636.887409] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 2762.360701] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 2762.365258] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 3415.608666] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 3416.010760] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 3478.856703] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 3478.933260] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 4522.354434] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 4522.359088] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 5916.180471] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 5916.185135] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 6078.058134] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 6078.062731] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 7495.014027] mtrr: your BIOS has configured an incorrect mask, fixing it.
[ 7495.018582] mtrr: your BIOS has configured an incorrect mask, fixing it.



```Please Help!

---

### Post by dzup on 2013-08-25
Mark this as SOLVED

PROS: CHROME does not hang up when playing videos from youtube
          No more Freezing so far.
          I got SOUND!

CONS: Right-Click on Mouse Pad does not work.
The touch keys MUTE, VOL UP/DOWN, CAMERA, NIGHT Does not work.

So far its been good, i wil keep updating as i test this machine a few more days.
 
My LENOVO z585 IdeaPad had sound now! this is what i did:

Update and Upgrade:
```

sudo apt-get update
sudo apt-get upgrade

```

Install ubuntu-restricted-extras
```

sudo apt-get install ubuntu-restricted-extras

```

Install this key and update
```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update

```

Download [FONT=arial][B]amd-driver-installer-catalyst-13-6-beta-x86.x86_64.zip from AMD.
(of course go ahead and get the Latest here: [/B][/FONT][http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx) )

Install
```

[FONT=arial]unzip amd-driver-installer-catalyst-13-6-beta-x86.x86_64.zip
sudo chmod +x amd-driver-installer-catalyst-13-6-beta-x86.x86_64.run
sudo apt-get remove fglrx
sudo ./amd-driver-installer-catalyst-13-6-beta-x86.x86_64.run[/FONT][COLOR=#555555][FONT=consolas]
[/FONT][/COLOR]
```[COLOR=#555555][FONT=consolas]

_[SIZE=4][FONT=arial black]Works in both i386 or amd64.[/FONT][/SIZE]_
[/FONT][/COLOR]

Execute
```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`

```
Reboot
```

sudo reboot

```

After rebooting:
```

cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; pacmd list-sinks; aplay -l; sudo alsa force-reload;  sudo lshw -C sound

```

Press Ctrl + C when finish, after a few seconds without any output (The important thing is you erase the .conf files and restart your alsa), then ...

```

sudo apt-get install alsa-firmware-loaders
sudo apt-get autoremove pulseaudio
sudo apt-get install gnome-alsamixer
sudo nano /etc/default/grub

```

In */etc/default/grub* **change**
> 
GRUB_CMDLINE_LINUX=""

to
> 
GRUB_CMDLINE_LINUX="edd=on nolapic radeon.audio=1"

Save and exit (Ctrl X + Y, Enter), update grub:
```

sudo update-grub

```

Install fglrx updates:
```

sudo apt-get install fglrx-amdcccle-updates

```

After rebooting, execute
```
alsamixer
```

And alter the master and other settings using arrow keys, Now you have sound.

I dont know if some of those steps are not necessary since i did this howto using my history file, but seems to work, please advice if you found any problem, thank you all.

---

### Post by dzup on 2013-08-29
The Right-click mouse pad has been solve by executing:
sudo su
cd /etc/modprobe.d
echo "options psmouse proto=exps" > /etc/modprobe.d/psmouse.modprobe

---

### Post by dzup on 2013-08-29
I change
GRUB_CMDLINE_LINUX="edd=off nolapic radeon.audio=1 acpi=on"
#GRUB_CMDLINE_LINUX="edd=on nolapic radeon.audio=1 acpi=on"

in /etc/default/grub and seems to boot faster

---

