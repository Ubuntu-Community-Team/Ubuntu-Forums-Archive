---
title: "New install 18.04 and it is slow"
date: 2019-11-04
forum: Installation &amp; Upgrades
---

### Post by kmd107 on 2019-11-04
Fresh install, no other OS, using SSD.  It is also slow running OS on USB.  It takes 2 seconds to see a item clicked or 2 seconds per letter pressed on keyboard for text entry.  Win10 was on PC before with no performance issues.  Older i5 with 8GB memory.  Not sure what the issue is. Any ideas?

```
brian-hp-elitedesk-800-g1-sff
    description: Low Profile Desktop Computer
    product: HP EliteDesk 800 G1 SFF (C8N26AV)
    vendor: Hewlett-Packard
    serial: MXL3461D4Q
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=low-profile family=103C_53307F G=D frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=C8N26AV uuid=8077DE70-4345-E311-BC48-7446A0B232C6
  *-core
       description: Motherboard
       product: 1998
       vendor: Hewlett-Packard
       physical id: 0
       serial: MXL3461D4Q
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: L01 v02.18
          date: 09/09/2013
          size: 64KiB
          capacity: 15MiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-4570 CPU @ 3.20GHz
          vendor: Intel Corp.
          physical id: 9
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-4570 CPU @ 3.20GHz
          slot: SOCKET 0
          size: 3585MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts md_clear flush_l1d cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L2 cache
             physical id: a
             slot: CPU Internal L2
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
             configuration: level=2
        *-cache:1
             description: L1 cache
             physical id: b
             slot: CPU Internal L1
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-back
             configuration: level=1
        *-cache:2
             description: L3 cache
             physical id: c
             slot: CPU Internal L3
             size: 6MiB
             capacity: 6MiB
             capabilities: internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 8JTF51264AZ-1G6E1
             vendor: Micron
             physical id: 0
             serial: 22371931
             slot: DIMM4
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: DIMM3
        *-bank:2
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 8JTF51264AZ-1G6E1
             vendor: Micron
             physical id: 2
             serial: 22182022
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             serial: [Empty]
             slot: DIMM1
     *-pci
          description: Host bridge
          product: 4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
          configuration: driver=hsw_uncore
          resources: irq:0
        *-pci
             description: PCI bridge
             product: Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:f7c00000-f7cfffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Caicos XTX [Radeon HD 8490 / R5 235X OEM]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:31 memory:e0000000-efffffff memory:f7c20000-f7c3ffff ioport:e000(size=256) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: Caicos HDMI Audio [Radeon HD 6450 / 7450/8450/8490 OEM / R5 230/235/235X OEM]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:29 memory:f7c40000-f7c43fff
        *-display
             description: Display controller
             product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=i915 latency=0
             resources: irq:30 memory:f7800000-f7bfffff memory:d0000000-dfffffff ioport:f000(size=64)
        *-multimedia:0
             description: Audio device
             product: Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:32 memory:f7d34000-f7d37fff
        *-usb:0
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:24 memory:f7d20000-f7d2ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.0.0-32-generic xhci-hcd
                physical id: 0
                bus info: usb@3
                logical name: usb3
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=15 speed=480Mbit/s
              *-usb:0 UNCLAIMED
                   description: Generic USB device
                   product: 802.11ac WLAN Adapter
                   vendor: Realtek
                   physical id: 1
                   bus info: usb@3:1
                   version: 2.00
                   serial: 00e04c000001
                   capabilities: usb-2.10
                   configuration: maxpower=500mA speed=480Mbit/s
              *-usb:1
                   description: Keyboard
                   product: USB Keyboard
                   vendor: Logitech
                   physical id: 3
                   bus info: usb@3:3
                   version: 64.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=90mA speed=2Mbit/s
              *-usb:2
                   description: Keyboard
                   product: 2.4G Keyboard Mouse
                   vendor: MOSART Semi.
                   physical id: b
                   bus info: usb@3:b
                   version: 1.02
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.0.0-32-generic xhci-hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 5.00
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-communication:0
             description: Communication controller
             product: 8 Series/C220 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:27 memory:f7d40000-f7d4000f
        *-communication:1
             description: Serial controller
             product: 8 Series/C220 Series Chipset Family KT Controller
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:19 ioport:f0e0(size=8) memory:f7d3e000-f7d3efff
        *-network
             description: Ethernet interface
             product: Ethernet Connection I217-LM
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eno1
             version: 04
             serial: 74:46:a0:b2:32:c6
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-4 ip=192.168.29.105 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:26 memory:f7d00000-f7d1ffff memory:f7d3d000-f7d3dfff ioport:f080(size=32)
        *-usb:1
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7d3c000-f7d3c3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.0.0-32-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.04
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
        *-multimedia:1
             description: Audio device
             product: 8 Series/C220 Series Chipset High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:28 memory:f7d30000-f7d33fff
        *-usb:2
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7d3b000-f7d3b3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.0.0-32-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.04
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: Q87 Express LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:25 ioport:f0d0(size=8) ioport:f0c0(size=4) ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f060(size=32) memory:f7d3a000-f7d3a7ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series/C220 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7d39000-f7d390ff ioport:f040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3500414CS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: CA12
             serial: 5VV0A4P7
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=f76ea94e
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: be2764c2-aa4b-7148-b202-48fd02956955
                size: 498MiB
                capacity: 500MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2018-09-24 17:31:22 filesystem=ntfs label=System Reserved modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 80410871-2a5c-454b-8035-79990f044f6c
                size: 465GiB
                capacity: 465GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2018-10-08 16:31:07 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SanDisk SSD PLUS
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 00RL
             serial: 182649805951
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=90e798d8
           *-volume
                description: Linux LVM Physical Volume partition
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                serial: kHVhRm-Uofy-yfZz-pNmu-oC88-HRDc-0acxbv
                size: 111GiB
                capacity: 111GiB
                capabilities: primary multi lvm2
  *-power UNCLAIMED
       product: Standard Efficiency
       physical id: 1
       capacity: 32768mWh
```

---

### Post by mörgæs on 2019-11-13
Hi, welcome to the fora.

The hardware is more than strong enough to run Ubuntu. A long shot: Have you considered updating the BIOS?

---

