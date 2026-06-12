---
title: "wireless not working on mini-laptop"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by solidarity on 2011-01-03
Hello.  New user to Linux.  I installed Ubuntu 10.04 LTS to a mini-laptop, but the built-in wireless card/chip is not working.  It worked under the previous OS, XP.  There is a switch on the case frame that enables it, but the active light did not turn on during installation.  I installed a second time and manually flicked the switch every one second to see if it needed human intervention, but to no avail.  

My next step was to try to update Ubuntu to see if it would help, so I inserted a Belkin USB wireless, but the connection was intermittent at best.  I believe the device is faulty.  A wired connection is impossible as I am sharing with my neighbor.  What should I do to help Ubuntu the internal wireless device?  

Here is the output of lshw:
```
  
    description: Notebook
    product: HP Mini
    vendor: Hewlett-Packard
    version: F.10
    serial: CNU9103JM8
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=1 uuid=E8310E5D-0CE1-02FF-5093-C9103789D0F7
  *-core
       description: Motherboard
       product: 361A
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 02.0E
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 361A0 Ver. F.10 (12/25/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU 1
          size: 800MHz
          capacity: 1666MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm pse cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 24KiB
             capacity: 24KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 1GiB
        *-bank
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:fe980000-fe9fffff ioport:dc80(size=8) memory:d0000000-dfffffff(prefetchable) memory:fe940000-fe97ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fe880000-fe8fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fe938000-fe93bfff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:1000(size=4096) memory:fea00000-feafffff memory:40000000-401fffff(prefetchable)
           *-network
                description: Network controller
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:16 memory:feafc000-feafffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:e000(size=4096) memory:feb00000-febfffff memory:40200000-403fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 88E8040 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 00
                serial: 00:24:81:4b:50:fb
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:26 memory:febfc000-febfffff ioport:ec00(size=256)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:dc00(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d880(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d800(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d480(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fe937c00-fe937fff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-disk
                description: ATA Disk
                product: SanDisk pSSD 16G
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SSD
                serial: CLZ030109204602
                size: 15GiB (16GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1bfc1bfc
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: d5991fa9-494d-4363-837e-a91e60c818e7
                   size: 3814MiB
                   capacity: 3814MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-01-02 11:41:16 filesystem=ext4 lastmountpoint=/Lï¿½0xï¿½ï¿½ï¿½ï¿½ï¿½ïï¿½ï¿½ï¿½ï¿½ï¿½pï¿½ï¿½u^ ï¿½U/ï¿½dï¿½ï¿½~!ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½xï¿½ï¿½Ì¾æ&#338;¾ï¿½a modified=2011-01-02 11:56:12 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-01-03 09:07:12 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 953MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 10GiB
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:24:2b:bd:6e:9e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

---

### Post by ajgreeny on 2011-01-03
I think you have to use ```
sudo lshw
``` to get the wireless card details; it certainly doesn't show on your output.

Try also ```
lspci
```which may help identify it.

---

### Post by solidarity on 2011-01-03
It's a Broadcom 4312. Apparently, drivers were written only for Windows, so ndiswrapper is needed to use it. 

```

$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common

```

When I tried that, it could not find the package.  I assume apt-get needs an internet connection.  This is the output of dmesg:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7b0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7b0000 - 000000003f7be000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f7be000 - 000000003f7f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7f0000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x3f7b0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-E3FFF write-protect
[    0.000000]   E4000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 0C0000000 write-back
[    0.000000]   1 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f7b0000 (usable)
[    0.000000]  modified: 000000003f7b0000 - 000000003f7be000 (ACPI data)
[    0.000000]  modified: 000000003f7be000 - 000000003f7f0000 (ACPI NVS)
[    0.000000]  modified: 000000003f7f0000 - 000000003f800000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2f26a000 - 2fa03412
[    0.000000] ACPI: RSDP 000f9c50 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3f7b0000 0003C (v01 122508 RSDT1024 20081225 MSFT 00000097)
[    0.000000] ACPI: FACP 3f7b0200 00084 (v02 122508 FACP1024 20081225 MSFT 00000097)
[    0.000000] ACPI: DSDT 3f7b0430 07F2B (v01  361A0 361A0F10 00000F10 INTL 20051117)
[    0.000000] ACPI: FACS 3f7be000 00040
[    0.000000] ACPI: APIC 3f7b0390 0005C (v01 122508 APIC1024 20081225 MSFT 00000097)
[    0.000000] ACPI: MCFG 3f7b03f0 0003C (v01 122508 OEMMCFG  20081225 MSFT 00000097)
[    0.000000] ACPI: OEMB 3f7be040 00224 (v01 122508 OEMB1024 20081225 MSFT 00000097)
[    0.000000] ACPI: ASF! 3f7b8360 00075 (v32 LEGEND I865PASF 00000001 INTL 20051117)
[    0.000000] ACPI: SSDT 3f7bebe0 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [002f26a000 - 002fa03412]          RAMDISK ==> [002f26a000 - 002fa03412]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd1b4]              BRK ==> [00008da000 - 00008dd1b4]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f7b0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f7b0
[    0.000000] On node 0 totalpages: 259915
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 256 pages used for memmap
[    0.000000]   HighMem zone: 32434 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:bf600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36024 r0 d21320 u2097152
[    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257883
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=d5991fa9-494d-4363-837e-a91e60c818e7 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5200320 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f7b0)
[    0.000000] Memory: 1009040k/1040064k available (4673k kernel code, 30004k reserved, 2122k data, 656k init, 130760k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.177 MHz processor.
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.35 BogoMIPS (lpj=6384708)
[    0.004047] Security Framework initialized
[    0.004090] AppArmor: AppArmor initialized
[    0.004107] Mount-cache hash table entries: 512
[    0.004351] Initializing cgroup subsys ns
[    0.004361] Initializing cgroup subsys cpuacct
[    0.004371] Initializing cgroup subsys memory
[    0.004385] Initializing cgroup subsys devices
[    0.004391] Initializing cgroup subsys freezer
[    0.004397] Initializing cgroup subsys net_cls
[    0.004435] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004442] CPU: L2 cache: 512K
[    0.004448] CPU: Physical Processor ID: 0
[    0.004452] CPU: Processor Core ID: 0
[    0.004459] mce: CPU supports 5 MCE banks
[    0.004476] CPU0: Thermal monitoring enabled (TM2)
[    0.004485] using mwait in idle threads.
[    0.004496] Performance Events: Atom events, Intel PMU driver.
[    0.004513] ... version:                3
[    0.004518] ... bit width:              40
[    0.004522] ... generic registers:      2
[    0.004527] ... value mask:             000000ffffffffff
[    0.004532] ... max period:             000000007fffffff
[    0.004537] ... fixed-purpose events:   3
[    0.004542] ... event mask:             0000000700000003
[    0.004551] Checking 'hlt' instruction... OK.
[    0.020009] Disabling 4MB page tables to avoid TLB bug
[    0.024422] ACPI: Core revision 20090903
[    0.044021] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.044037] ftrace: allocating 21771 entries in 43 pages
[    0.048108] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.048482] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.088913] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.092001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.176071] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.176099] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.180035] Brought up 2 CPUs
[    0.180042] Total of 2 processors activated (6384.48 BogoMIPS).
[    0.180285] CPU0 attaching sched-domain:
[    0.180294]  domain 0: span 0-1 level SIBLING
[    0.180300]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.180312]   domain 1: span 0-1 level MC
[    0.180318]    groups: 0-1 (cpu_power = 1178)
[    0.180330] CPU1 attaching sched-domain:
[    0.180335]  domain 0: span 0-1 level SIBLING
[    0.180340]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.180352]   domain 1: span 0-1 level MC
[    0.180357]    groups: 0-1 (cpu_power = 1178)
[    0.180589] devtmpfs: initialized
[    0.180589] regulator: core version 0.5
[    0.180589] Time: 17:07:08  Date: 01/03/11
[    0.180589] NET: Registered protocol family 16
[    0.180589] Trying to unpack rootfs image as initramfs...
[    0.180589] EISA bus registered
[    0.180602] ACPI: bus type pci registered
[    0.180773] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.180783] PCI: Not using MMCONFIG.
[    0.181101] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.181108] PCI: Using configuration type 1 for base access
[    0.186174] bio: create slab <bio-0> at 0
[    0.188499] ACPI: EC: Look up EC in DSDT
[    0.191398] ACPI: BIOS _OSI(Linux) query ignored
[    0.193628] ACPI: Executed 1 blocks of module-level executable AML code
[    0.420108] ACPI: Interpreter enabled
[    0.420129] ACPI: (supports S0 S3 S4 S5)
[    0.420199] ACPI: Using IOAPIC for interrupt routing
[    0.420342] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.437408] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.437408] PCI: updated MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.437408] PCI: Using MMCONFIG for extended config space
[    0.456488] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.457053] ACPI: No dock devices found.
[    0.457539] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.457748] pci 0000:00:02.0: reg 10 32bit mmio: [0xfe980000-0xfe9fffff]
[    0.457761] pci 0000:00:02.0: reg 14 io port: [0xdc80-0xdc87]
[    0.457774] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.457787] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfe940000-0xfe97ffff]
[    0.457857] pci 0000:00:02.1: reg 10 32bit mmio: [0xfe880000-0xfe8fffff]
[    0.458009] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe938000-0xfe93bfff]
[    0.458085] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.458097] pci 0000:00:1b.0: PME# disabled
[    0.458221] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.458234] pci 0000:00:1c.0: PME# disabled
[    0.458359] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.458370] pci 0000:00:1c.1: PME# disabled
[    0.458462] pci 0000:00:1d.0: reg 20 io port: [0xdc00-0xdc1f]
[    0.458549] pci 0000:00:1d.1: reg 20 io port: [0xd880-0xd89f]
[    0.458636] pci 0000:00:1d.2: reg 20 io port: [0xd800-0xd81f]
[    0.458723] pci 0000:00:1d.3: reg 20 io port: [0xd480-0xd49f]
[    0.458819] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe937c00-0xfe937fff]
[    0.458903] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.458915] pci 0000:00:1d.7: PME# disabled
[    0.459139] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.459156] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.459167] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.459177] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0500 (mask 0003)
[    0.459189] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
[    0.459269] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.459285] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.459300] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[    0.459315] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[    0.459330] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.459430] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.459693] pci 0000:01:00.0: reg 10 64bit mmio: [0xfeafc000-0xfeafffff]
[    0.459930] pci 0000:01:00.0: supports D1 D2
[    0.460114] pci 0000:00:1c.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.460579] pci 0000:02:00.0: reg 10 64bit mmio: [0xfebfc000-0xfebfffff]
[    0.460637] pci 0000:02:00.0: reg 18 io port: [0xec00-0xecff]
[    0.461125] pci 0000:02:00.0: supports D1 D2
[    0.461133] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.461163] pci 0000:02:00.0: PME# disabled
[    0.461379] pci 0000:00:1c.1: bridge io port: [0xe000-0xefff]
[    0.461390] pci 0000:00:1c.1: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.461481] pci 0000:00:1e.0: transparent bridge
[    0.461529] pci_bus 0000:00: on NUMA node 0
[    0.461554] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.461954] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.462520] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.491073] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.491385] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.491712] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.492059] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.492368] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.492702] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.493016] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.493326] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.493670] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.493701] vgaarb: loaded
[    0.494045] SCSI subsystem initialized
[    0.494314] libata version 3.00 loaded.
[    0.494580] usbcore: registered new interface driver usbfs
[    0.494651] usbcore: registered new interface driver hub
[    0.494753] usbcore: registered new device driver usb
[    0.495332] ACPI: WMI: Mapper loaded
[    0.495339] PCI: Using ACPI for IRQ routing
[    0.495867] NetLabel: Initializing
[    0.495874] NetLabel:  domain hash size = 128
[    0.495879] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.495914] NetLabel:  unlabeled traffic allowed by default
[    0.496212] hpet clockevent registered
[    0.496222] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.496235] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.496250] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.500064] Switching to clocksource tsc
[    0.505050] AppArmor: AppArmor Filesystem Enabled
[    0.505098] pnp: PnP ACPI init
[    0.505148] ACPI: bus type pnp registered
[    0.510869] pnp: PnP ACPI: found 12 devices
[    0.510879] ACPI: ACPI bus type pnp unregistered
[    0.510889] PnPBIOS: Disabled by ACPI PNP
[    0.510928] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    0.510958] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.510968] system 00:08: ioport range 0x500-0x501 has been reserved
[    0.510978] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.510988] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.510999] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.511010] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.511020] system 00:08: iomem range 0xfed40000-0xfed8ffff has been reserved
[    0.511041] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.511051] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.511071] system 00:0a: iomem range 0xe0000000-0xe3ffffff has been reserved
[    0.511091] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.511102] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.511113] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.511124] system 00:0b: iomem range 0x100000-0x3f7fffff could not be reserved
[    0.511136] system 00:0b: iomem range 0xfed90000-0xffffffff could not be reserved
[    0.546365] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.546379] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.546392] pci 0000:00:1c.0:   MEM window: 0xfea00000-0xfeafffff
[    0.546403] pci 0000:00:1c.0:   PREFETCH window: 0x00000040000000-0x000000401fffff
[    0.546418] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.546428] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
[    0.546440] pci 0000:00:1c.1:   MEM window: 0xfeb00000-0xfebfffff
[    0.546451] pci 0000:00:1c.1:   PREFETCH window: 0x00000040200000-0x000000403fffff
[    0.546466] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.546472] pci 0000:00:1e.0:   IO window: disabled
[    0.546483] pci 0000:00:1e.0:   MEM window: disabled
[    0.546492] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.546523] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[    0.546547]   alloc irq_desc for 16 on node -1
[    0.546554]   alloc kstat_irqs on node -1
[    0.546572] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.546586] pci 0000:00:1c.0: setting latency timer to 64
[    0.546609]   alloc irq_desc for 17 on node -1
[    0.546616]   alloc kstat_irqs on node -1
[    0.546629] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.546642] pci 0000:00:1c.1: setting latency timer to 64
[    0.546659] pci 0000:00:1e.0: setting latency timer to 64
[    0.546673] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.546683] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.546693] pci_bus 0000:01: resource 0 io:  [0x1000-0x1fff]
[    0.546703] pci_bus 0000:01: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.546712] pci_bus 0000:01: resource 2 pref mem [0x40000000-0x401fffff]
[    0.546721] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.546730] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.546740] pci_bus 0000:02: resource 2 pref mem [0x40200000-0x403fffff]
[    0.546749] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.546758] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.546855] NET: Registered protocol family 2
[    0.547133] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.548103] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.549290] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.549841] TCP: Hash tables configured (established 131072 bind 65536)
[    0.549850] TCP reno registered
[    0.550185] NET: Registered protocol family 1
[    0.550244] pci 0000:00:02.0: Boot video device
[    0.550988] cpufreq-nforce2: No nForce2 chipset.
[    0.551071] Scanning for low memory corruption every 60 seconds
[    0.551449] audit: initializing netlink socket (disabled)
[    0.551479] type=2000 audit(1294074427.551:1): initialized
[    0.572982] highmem bounce pool size: 64 pages
[    0.573003] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.578349] VFS: Disk quotas dquot_6.5.2
[    0.578553] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.580621] fuse init (API version 7.13)
[    0.580905] msgmni has been set to 1716
[    0.581597] alg: No test for stdrng (krng)
[    0.581789] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.581798] io scheduler noop registered
[    0.581804] io scheduler anticipatory registered
[    0.581810] io scheduler deadline registered
[    0.581947] io scheduler cfq registered (default)
[    0.582281]   alloc irq_desc for 24 on node -1
[    0.582289]   alloc kstat_irqs on node -1
[    0.582310] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.582328] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.582597]   alloc irq_desc for 25 on node -1
[    0.582604]   alloc kstat_irqs on node -1
[    0.582621] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.582638] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.582863] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.583097] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.584965] ACPI: AC Adapter [AC0] (on-line)
[    0.585270] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C0D:00/input/input0
[    0.585819] ACPI: Lid Switch [LID]
[    0.585974] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.585985] ACPI: Sleep Button [SLPB]
[    0.586128] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.586137] ACPI: Power Button [PWRB]
[    0.586279] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.586288] ACPI: Power Button [PWRF]
[    0.588150] ACPI: SSDT 3f7be340 0023C (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.589370] ACPI: SSDT 3f7be610 005D0 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.590385] Monitor-Mwait will be used to enter C-1 state
[    0.590495] Monitor-Mwait will be used to enter C-2 state
[    0.590587] Monitor-Mwait will be used to enter C-3 state
[    0.590608] Marking TSC unstable due to TSC halts in idle
[    0.590756] processor LNXCPU:00: registered as cooling_device0
[    0.591193] ACPI: SSDT 3f7be270 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.591193] ACPI: SSDT 3f7be580 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.592166] Switching to clocksource hpet
[    0.600574] processor LNXCPU:01: registered as cooling_device1
[    0.609178] thermal LNXTHERM:01: registered as thermal_zone0
[    0.609205] ACPI: Thermal Zone [THRM] (20 C)
[    0.612726] Freeing initrd memory: 7781k freed
[    0.617228] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.621104] isapnp: Scanning for PnP cards...
[    0.623392] brd: module loaded
[    0.624882] loop: module loaded
[    0.625159] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.625413] ata_piix 0000:00:1f.1: version 2.13
[    0.625442]   alloc irq_desc for 18 on node -1
[    0.625449]   alloc kstat_irqs on node -1
[    0.625465] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.625544] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.625909] scsi0 : ata_piix
[    0.626517] scsi1 : ata_piix
[    0.630487] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.630496] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.633059] Fixed MDIO Bus: probed
[    0.633170] PPP generic driver version 2.4.2
[    0.633309] tun: Universal TUN/TAP device driver, 1.6
[    0.633315] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.633554] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.633675]   alloc irq_desc for 23 on node -1
[    0.633681]   alloc kstat_irqs on node -1
[    0.633697] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.633940] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.633950] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.634064] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.634109] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.634130] ehci_hcd 0000:00:1d.7: debug port 1
[    0.638012] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.638070] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe937c00
[    0.642183] ata2: port disabled. ignoring.
[    0.645808] ACPI: Battery Slot [BAT1] (battery present)
[    0.652033] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.652296] usb usb1: configuration #1 chosen from 1 choice
[    0.652382] hub 1-0:1.0: USB hub found
[    0.652411] hub 1-0:1.0: 8 ports detected
[    0.652582] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.652629] uhci_hcd: USB Universal Host Controller Interface driver
[    0.652706] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.652723] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.652732] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.652834] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.652879] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000dc00
[    0.653139] usb usb2: configuration #1 chosen from 1 choice
[    0.653226] hub 2-0:1.0: USB hub found
[    0.653245] hub 2-0:1.0: 2 ports detected
[    0.653364]   alloc irq_desc for 19 on node -1
[    0.653371]   alloc kstat_irqs on node -1
[    0.653386] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.653402] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.653410] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.653503] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.653558] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d880
[    0.653818] usb usb3: configuration #1 chosen from 1 choice
[    0.653902] hub 3-0:1.0: USB hub found
[    0.653921] hub 3-0:1.0: 2 ports detected
[    0.654031] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.654045] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.654054] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.654149] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.654204] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    0.654462] usb usb4: configuration #1 chosen from 1 choice
[    0.654540] hub 4-0:1.0: USB hub found
[    0.654559] hub 4-0:1.0: 2 ports detected
[    0.654669] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.654684] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.654692] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.654794] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.654849] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d480
[    0.655097] usb usb5: configuration #1 chosen from 1 choice
[    0.655175] hub 5-0:1.0: USB hub found
[    0.655194] hub 5-0:1.0: 2 ports detected
[    0.655439] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.659142] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.661755] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.661780] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.661871] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.661943] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.662034] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.662382] mice: PS/2 mouse device common for all mice
[    0.662813] rtc_cmos 00:03: RTC can wake from S4
[    0.662929] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.662974] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.663301] device-mapper: uevent: version 1.0.3
[    0.663616] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.663834] device-mapper: multipath: version 1.1.0 loaded
[    0.663843] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.664218] EISA: Probing bus 0 at eisa.0
[    0.664233] Cannot allocate resource for EISA slot 1
[    0.664271] EISA: Detected 0 cards.
[    0.664710] cpuidle: using governor ladder
[    0.665051] cpuidle: using governor menu
[    0.666329] TCP cubic registered
[    0.666830] NET: Registered protocol family 10
[    0.668116] lo: Disabled Privacy Extensions
[    0.669029] NET: Registered protocol family 17
[    0.670073] Using IPI No-Shortcut mode
[    0.670338] PM: Resume from disk failed.
[    0.670380] registered taskstats version 1
[    0.671231]   Magic number: 11:61:137
[    0.671262] block ram2: hash matches
[    0.671375] rtc_cmos 00:03: setting system clock to 2011-01-03 17:07:08 UTC (1294074428)
[    0.671384] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.671389] EDD information not available.
[    0.695607] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.784617] ata1.00: CFA: SanDisk pSSD 16GB, SSD 4.46, max UDMA/66
[    0.784627] ata1.00: 32014080 sectors, multi 0: LBA 
[    0.785249] ata1.00: configured for UDMA/66
[    0.964044] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    0.974805] isapnp: No Plug & Play device found
[    0.975044] scsi 0:0:0:0: Direct-Access     ATA      SanDisk pSSD 16G SSD  PQ: 0 ANSI: 5
[    0.975351] sd 0:0:0:0: [sda] 32014080 512-byte logical blocks: (16.3 GB/15.2 GiB)
[    0.975395] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.975536] sd 0:0:0:0: [sda] Write Protect is off
[    0.975547] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.975647] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.976015]  sda: sda1 sda2 < sda5 sda6 >
[    0.980366] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.980398] Freeing unused kernel memory: 656k freed
[    0.980990] Write protecting the kernel text: 4676k
[    0.981099] Write protecting the kernel read-only data: 1840k
[    1.019766] udev: starting version 151
[    1.135815] usb 1-4: configuration #1 chosen from 1 choice
[    1.320817] sky2 driver version 1.25
[    1.321006] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.321069] sky2 0000:02:00.0: setting latency timer to 64
[    1.321205] sky2 0000:02:00.0: Yukon-2 FE+ chip revision 0
[    1.321807]   alloc irq_desc for 26 on node -1
[    1.321815]   alloc kstat_irqs on node -1
[    1.321903] sky2 0000:02:00.0: irq 26 for MSI/MSI-X
[    1.351712] sky2 eth0: addr 00:24:81:4b:50:fb
[    1.371999] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.372028] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[    1.398115] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    1.438069] ssb: Sonics Silicon Backplane found on PCI device 0000:01:00.0
[    5.060762] Adding 975864k swap on /dev/sda5.  Priority:-1 extents:1 across:975864k 
[    5.147259] udev: starting version 151
[    5.300916] lp: driver loaded but no devices found
[    5.500820] Linux agpgart interface v0.103
[    5.623032] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    5.623171] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[    5.647988] intel_rng: FWH not detected
[    5.871904] cfg80211: Calling CRDA to update world regulatory domain
[    5.909581] type=1505 audit(1294074433.736:2):  operation="profile_load" pid=537 name="/sbin/dhclient3"
[    5.910387] type=1505 audit(1294074433.736:3):  operation="profile_load" pid=537 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    5.910863] type=1505 audit(1294074433.736:4):  operation="profile_load" pid=537 name="/usr/lib/connman/scripts/dhclient-script"
[    5.911830] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    5.912125] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    5.915129] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    6.018006] cfg80211: World regulatory domain updated:
[    6.018016]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    6.018027]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.018036]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.018045]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.018054]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.018063]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.041062] Linux video capture interface: v2.00
[    6.085730] [drm] Initialized drm 1.1.0 20060810
[    6.218950] uvcvideo: Found UVC 1.00 device Webcam-101 (10f1:1a08)
[    6.251659] input: Webcam-101 as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input7
[    6.251855] usbcore: registered new interface driver uvcvideo
[    6.251867] USB Video Class driver (v0.1.0)
[    6.297273] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    6.503230] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.503247] i915 0000:00:02.0: setting latency timer to 64
[    6.557952] [drm] set up 7M of stolen space
[    6.635067] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04711/0xa00000
[    6.635774] phy0: Selected rate control algorithm 'minstrel'
[    6.637853] Registered led device: b43-phy0::tx
[    6.637907] Registered led device: b43-phy0::rx
[    6.637961] Registered led device: b43-phy0::radio
[    6.638127] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[    6.678424] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[    6.685718] [drm] initialized overlay support
[    6.800147] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[    6.891282] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[    6.944164] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[    6.944295] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[    6.944420] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[    6.955926] sky2 eth0: enabling interface
[    6.959390] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.005758] type=1505 audit(1294074434.832:5):  operation="profile_load" pid=714 name="/usr/share/gdm/guest-session/Xsession"
[    7.011003] type=1505 audit(1294074434.836:6):  operation="profile_replace" pid=715 name="/sbin/dhclient3"
[    7.014278] type=1505 audit(1294074434.840:7):  operation="profile_replace" pid=715 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    7.014758] type=1505 audit(1294074434.840:8):  operation="profile_replace" pid=715 name="/usr/lib/connman/scripts/dhclient-script"
[    7.023409] type=1505 audit(1294074434.848:9):  operation="profile_load" pid=716 name="/usr/bin/evince"
[    7.030980] type=1505 audit(1294074434.856:10):  operation="profile_load" pid=716 name="/usr/bin/evince-previewer"
[    7.035778] type=1505 audit(1294074434.860:11):  operation="profile_load" pid=716 name="/usr/bin/evince-thumbnailer"
[    7.036231] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[    7.043565] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[    7.050236] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[    7.050320] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[    7.050400] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[    7.155276] fb0: inteldrmfb frame buffer device
[    7.155285] registered panic notifier
[    7.155306] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.155406] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.155472] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.165874] vga16fb: initializing
[    7.165886] vga16fb: mapped to 0xc00a0000
[    7.165897] vga16fb: not registering due to another framebuffer present
[    7.264958] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[    7.293990] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    7.294402] input: HDA Intel Mic at Sep Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    7.294752] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    7.295159] input: HDA Intel HP Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    7.450822] Console: switching to colour frame buffer device 128x37
[    7.857419] ppdev: user-space parallel port driver
[  691.680295] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  691.985340] usb 1-1: configuration #1 chosen from 1 choice
[  692.167654] phy1: Selected rate control algorithm 'minstrel'
[  692.172324] Registered led device: rt2500usb-phy1::radio
[  692.172546] Registered led device: rt2500usb-phy1::quality
[  692.174079] usbcore: registered new interface driver rt2500usb
[  692.202471] usbcore: registered new interface driver rt73usb
[  692.226455] usbcore: registered new interface driver p54usb
[  692.443940] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  700.000537] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[  700.000620] wlan1: deauthenticating from 00:17:9a:cd:5d:bc by local choice (reason=3)
[  700.000786] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[  700.003687] wlan1: direct probe responded
[  700.003697] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[  700.007533] wlan1: authenticated
[  700.007592] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[  700.011176] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=2)
[  700.011187] wlan1: associated
[  700.016718] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  700.016831] cfg80211: Calling CRDA for country: US
[  700.026414] cfg80211: Received country IE:
[  700.026425] cfg80211: Regulatory domain: US
[  700.026431]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  700.026442]     (2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[  700.026448] cfg80211: CRDA thinks this should applied:
[  700.026454] cfg80211: Regulatory domain: US
[  700.026459]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  700.026469]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  700.026478]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  700.026488]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  700.026497]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  700.026506]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  700.026515]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  700.026520] cfg80211: We intersect both of these and get:
[  700.026526] cfg80211: Regulatory domain: 98
[  700.026531]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  700.026540]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  700.026555] cfg80211: Disabling channel 2467 MHz on phy1 due to Country IE
[  700.026565] cfg80211: Disabling channel 2472 MHz on phy1 due to Country IE
[  700.026572] cfg80211: Disabling channel 2484 MHz on phy1 due to Country IE
[  700.026588] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[  700.026596] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[  700.026604] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[  700.026614] cfg80211: Current regulatory domain updated by AP to: US
[  700.026620]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  700.026630]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  701.101948] padlock: VIA PadLock not detected.
[  706.493127] No probe response from AP 00:17:9a:cd:5d:bc after 500ms, disconnecting.
[  707.511530] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[  707.708161] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 2)
[  707.908144] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 3)
[  708.108114] wlan1: direct probe to AP 00:17:9a:cd:5d:bc timed out
[  710.168105] wlan1: no IPv6 routers present
[  747.553672] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[  747.752139] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 2)
[  747.754581] wlan1: direct probe responded
[  747.754597] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[  747.758337] wlan1: authenticated
[  747.758419] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[  747.957102] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 2)
[  748.156166] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 3)
[  748.356126] wlan1: association with AP 00:17:9a:cd:5d:bc timed out
[  761.545925] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[  761.548378] wlan1: direct probe responded
[  761.548403] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[  761.550194] wlan1: authenticated
[  761.550303] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[  761.553731] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=2)
[  761.553753] wlan1: associated
[  844.492095] No probe response from AP 00:17:9a:cd:5d:bc after 500ms, disconnecting.
[  845.514419] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[  845.521598] wlan1: direct probe responded
[  845.521612] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[  845.721161] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 2)
[  845.921116] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 3)
[  846.121147] wlan1: authentication with AP 00:17:9a:cd:5d:bc timed out
[  862.225911] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[  862.425071] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 2)
[  862.427453] wlan1: direct probe responded
[  862.427466] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[  862.433243] wlan1: authenticated
[  862.433313] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[  862.441199] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=2)
[  862.441211] wlan1: associated
[  909.492131] No probe response from AP 00:17:9a:cd:5d:bc after 500ms, disconnecting.
[  945.548818] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[  945.551271] wlan1: direct probe responded
[  945.551293] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[  945.749138] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 2)
[  945.948164] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 3)
[  946.148126] wlan1: authentication with AP 00:17:9a:cd:5d:bc timed out
[  973.920191] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[  974.120150] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 2)
[  974.320134] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 3)
[  974.520130] wlan1: direct probe to AP 00:17:9a:cd:5d:bc timed out
[ 1254.943700] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 1254.946015] wlan1: direct probe responded
[ 1254.946027] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[ 1254.947748] wlan1: authenticated
[ 1254.947808] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[ 1254.950899] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=2)
[ 1254.950909] wlan1: associated
[ 1268.492131] No probe response from AP 00:17:9a:cd:5d:bc after 500ms, disconnecting.
[ 1269.509612] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 1269.708172] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 2)
[ 1269.908132] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 3)
[ 1270.108136] wlan1: direct probe to AP 00:17:9a:cd:5d:bc timed out
[ 1280.367252] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 1280.369648] wlan1: direct probe responded
[ 1280.369666] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[ 1280.371797] wlan1: authenticated
[ 1280.371869] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[ 1280.374920] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=2)
[ 1280.374941] wlan1: associated
[ 1283.833701] wlan1: deauthenticated from 00:17:9a:cd:5d:bc (Reason: 6)
[ 1284.831837] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 1285.028095] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 2)
[ 1285.228158] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 3)
[ 1285.428116] wlan1: direct probe to AP 00:17:9a:cd:5d:bc timed out
[ 1295.950046] usb 1-1: USB disconnect, address 3
[ 1305.825234] usb 1-1: new high speed USB device using ehci_hcd and address 4
[ 1306.130378] usb 1-1: configuration #1 chosen from 1 choice
[ 1306.242695] cfg80211: Disabling channel 2467 MHz on phy2 due to Country IE
[ 1306.242715] cfg80211: Disabling channel 2472 MHz on phy2 due to Country IE
[ 1306.242732] cfg80211: Disabling channel 2484 MHz on phy2 due to Country IE
[ 1306.245118] phy2: Selected rate control algorithm 'minstrel'
[ 1306.254478] Registered led device: rt2500usb-phy2::radio
[ 1306.254613] Registered led device: rt2500usb-phy2::quality
[ 1306.469805] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1313.219966] wlan1: deauthenticating from 00:17:9a:cd:5d:bc by local choice (reason=3)
[ 1313.246713] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 1313.444164] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 2)
[ 1313.644165] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 3)
[ 1313.646548] wlan1: direct probe responded
[ 1313.646565] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[ 1313.648276] wlan1: authenticated
[ 1313.648365] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[ 1313.651405] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=2)
[ 1313.651420] wlan1: associated
[ 1313.662134] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1323.896099] wlan1: no IPv6 routers present
[ 1424.495619] No probe response from AP 00:17:9a:cd:5d:bc after 500ms, disconnecting.
[ 1425.522493] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 1425.721139] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 2)
[ 1425.920098] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 3)
[ 1426.120110] wlan1: direct probe to AP 00:17:9a:cd:5d:bc timed out
[ 1442.212011] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 1442.214403] wlan1: direct probe responded
[ 1442.214416] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[ 1442.216765] wlan1: authenticated
[ 1442.216827] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[ 1442.413079] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 2)
[ 1442.417150] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=2)
[ 1442.417162] wlan1: associated
[ 1476.492128] No probe response from AP 00:17:9a:cd:5d:bc after 500ms, disconnecting.
[ 1483.341647] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 1483.344093] wlan1: direct probe responded
[ 1483.344115] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[ 1483.345785] wlan1: authenticated
[ 1483.345838] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[ 1483.348755] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=2)
[ 1483.348767] wlan1: associated
[ 1774.317573] wlan1: deauthenticating from 00:17:9a:cd:5d:bc by local choice (reason=3)
[ 1774.529814] wlan1: deauthenticating from 00:17:9a:cd:5d:bc by local choice (reason=3)
[ 1774.731141] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 1774.737314] wlan1: direct probe responded
[ 1774.737325] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[ 1774.739134] wlan1: authenticated
[ 1774.739207] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[ 1774.742187] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=2)
[ 1774.742198] wlan1: associated
[ 3002.492160] No probe response from AP 00:17:9a:cd:5d:bc after 500ms, disconnecting.
[ 3003.509711] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 3003.512135] wlan1: direct probe responded
[ 3003.512156] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[ 3003.708131] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 2)
[ 3003.709799] wlan1: authenticated
[ 3003.709906] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[ 3003.712874] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=2)
[ 3003.712889] wlan1: associated
[ 3006.762980] wlan1: deauthenticated from 00:17:9a:cd:5d:bc (Reason: 2)
[ 3007.743624] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 3007.746135] wlan1: direct probe responded
[ 3007.746153] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[ 3007.945151] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 2)
[ 3007.950745] wlan1: authenticated
[ 3007.950828] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[ 3007.953638] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=2)
[ 3007.953647] wlan1: associated
[ 3010.991402] wlan1: deauthenticated from 00:17:9a:cd:5d:bc (Reason: 2)
[ 3011.974006] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 3012.172144] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 2)
[ 3012.373117] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 3)
[ 3012.572179] wlan1: direct probe to AP 00:17:9a:cd:5d:bc timed out
[ 3048.552141] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 3048.558379] wlan1: direct probe responded
[ 3048.558397] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[ 3048.560145] wlan1: authenticated
[ 3048.560239] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[ 3048.562764] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=5)
[ 3048.562789] wlan1: associated
[ 3051.611158] wlan1: deauthenticated from 00:17:9a:cd:5d:bc (Reason: 2)
[ 3052.611349] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 3052.613779] wlan1: direct probe responded
[ 3052.613799] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[ 3052.615602] wlan1: authenticated
[ 3052.615680] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[ 3052.618524] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=5)
[ 3052.618545] wlan1: associated
[ 3055.698412] wlan1: deauthenticated from 00:17:9a:cd:5d:bc (Reason: 2)
[ 3056.691203] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 3056.705059] wlan1: direct probe responded
[ 3056.705078] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[ 3056.706760] wlan1: authenticated
[ 3056.706838] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[ 3056.712015] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=5)
[ 3056.712030] wlan1: associated
[ 3059.762414] wlan1: deauthenticated from 00:17:9a:cd:5d:bc (Reason: 2)
[ 3060.765590] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 3060.965310] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 2)
[ 3060.972303] wlan1: direct probe responded
[ 3060.972321] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[ 3061.172105] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 2)
[ 3061.177649] wlan1: authenticated
[ 3061.177735] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[ 3061.180267] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=5)
[ 3061.180282] wlan1: associated
[ 3064.242414] wlan1: deauthenticated from 00:17:9a:cd:5d:bc (Reason: 2)
[ 3065.239460] wlan1: direct probe to AP 00:17:9a:cd:5d:bc (try 1)
[ 3065.243662] wlan1: direct probe responded
[ 3065.243685] wlan1: authenticate with AP 00:17:9a:cd:5d:bc (try 1)
[ 3065.246419] wlan1: authenticated
[ 3065.246538] wlan1: associate with AP 00:17:9a:cd:5d:bc (try 1)
[ 3065.250450] wlan1: RX AssocResp from 00:17:9a:cd:5d:bc (capab=0x431 status=0 aid=5)
[ 3065.250471] wlan1: associated
[ 3169.979695] usb 1-1: USB disconnect, address 4
[ 3169.989406] wlan1: deauthenticating from 00:17:9a:cd:5d:bc by local choice (reason=3)
[ 4007.720140] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 4007.855783] usb 1-1: configuration #1 chosen from 1 choice
[ 4007.998861] Initializing USB Mass Storage driver...
[ 4007.999216] scsi2 : SCSI emulation for USB Mass Storage devices
[ 4007.999730] usbcore: registered new interface driver usb-storage
[ 4007.999742] USB Mass Storage support registered.
[ 4008.002325] usb-storage: device found at 5
[ 4008.002334] usb-storage: waiting for device to settle before scanning
[ 4013.000625] usb-storage: device scan complete
[ 4013.001955] scsi 2:0:0:0: Direct-Access     USB 2.0  PenDrive              PQ: 0 ANSI: 0 CCS
[ 4013.008436] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 4013.009955] sd 2:0:0:0: [sdb] 1983999 512-byte logical blocks: (1.01 GB/968 MiB)
[ 4013.018155] sd 2:0:0:0: [sdb] Write Protect is off
[ 4013.018168] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 4013.018176] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 4013.026688] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 4013.026704]  sdb: sdb1
[ 4013.035566] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 4013.035582] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 4717.275390] usb 1-1: USB disconnect, address 5

```

---

### Post by solidarity on 2011-01-03
I found the webpage ["Install Broadcom 43xx Wireless Driver and Ndiswrapper in Feisty"]("http://www.stchman.com/install_ndis_broadcom.html") taken from the [Ubuntu Guide]("http://www.ubuntuguide.org/"), successfully downloaded the .inf file, extracted it to the Ubuntu computer via thumbdrive, but got a different result than the instructions.  Whereas the webpage says:

> 
Next you will need to execute the scripts, to do this type the following:
sudo ./ndiswrapper_setup

You can remove the files that were decompressed from the tar archive as they are no longer needed.

Reboot the machine and your wireless card should work.


I got:

```

sudo ./ndiswrapper_setup

./ndiswrapper_setup: 1: Syntax error: Unterminated quoted string

```

---

### Post by solidarity on 2011-01-03
Could a moderator move this thread to the networking subforum, please?

---

