---
title: "Can't upgrade or install past Feisty"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by ricardisimo on 2008-04-30
Exactly what the title says: I tried upgrading Ubuntu via Update Manager, which proved faulty after that first reboot. I can't recall now if anything happened at all. I got maybe a desktop background, but no icons with which to interact, nor any keyboard functionality. I then tried a fresh LiveCD install of first Ubuntu 7.10 and then Kubuntu 7.10. Neither gives me more than a nice-looking - albeit completely useless - LiveCD default desktop. No "Install" icon appears on the desktop, by the way, and the toolbar application launchers don't work, either. Below are my specs, via "sudo lshw".

The only other thing I can think of that's out of the ordinary is that CMOS battery is shot, and has been for some time now. It doesn't seem to me that this would affect install, though... or could it?

This is particularly saddening since my other comp at work is also stuck on Feisty because of its RaLink wireless card. But that's another story, even more exasperating than this one. Thanks in advance for any help.

```
description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P4P8X
       vendor: ASUSTek Computer Inc.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
       slot: 
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1006.007 (05/13/2003)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: CPU 1
          size: 2400MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 8KB
             capacity: 8KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KB
             capacity: 512KB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
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
          physical id: 35
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 256MB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 256MB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: f8000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f8000000-fbffffff
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200 SE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:e8000000-efffffff ioport:c000-c0ff iomemory:fe9f0000-fe9fffff irq:19
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 SE] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:e0000000-e7ffffff iomemory:fe9e0000-fe9effff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ef00-ef1f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ef20-ef3f irq:20
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Keyboard
                   product: Logitech USB Keyboard
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@3:1
                   version: 28.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ef40-ef5f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ef80-ef9f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:febffc00-febfffff irq:18
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb
                   description: Printer
                   product: Photosmart C5100 series
                   vendor: HP
                   physical id: 2
                   bus info: usb@1:2
                   logical name: scsi2
                   version: 1.00
                   serial: MY74PP604N04MK
                   capabilities: usb-2.00 bidirectional emulated scsi-host
                   configuration: driver=usb-storage maxpower=2mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: Photosmart C5180
                      vendor: HP
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sdc
                      version: 1.00
                      capabilities: removable
                      configuration: ansiversion=2
                    *-disc
                         physical id: 0
                         logical name: /dev/sdc
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network:0
                description: Ethernet interface
                product: 3c940 10/100/1000Base-T [Marvell]
                vendor: 3Com Corporation
                physical id: 5
                bus info: pci@02:05.0
                logical name: eth0
                version: 12
                serial: 00:0c:6e:58:94:61
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.9 duplex=full firmware=N/A ip=192.168.1.64 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100MB/s
                resources: iomemory:feaf8000-feafbfff ioport:d800-d8ff irq:21
           *-communication
                description: Modem
                product: HSP MicroModem 56
                vendor: PCTel Inc
                physical id: 9
                bus info: pci@02:09.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: hayes_16750 cap_list
                configuration: driver=serial latency=0
                resources: ioport:df00-df3f irq:16
           *-network:1
                description: Wireless interface
                product: ACX 100 22Mbps Wireless Interface
                vendor: Texas Instruments
                physical id: b
                bus info: pci@02:0b.0
                logical name: wlan0
                version: 00
                serial: 00:40:05:52:8f:54
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=acx_pci latency=64 multicast=yes wireless=IEEE 802.11b+
                resources: ioport:df80-df9f iomemory:feafe000-feafefff iomemory:fead0000-feadffff irq:18
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:fc00-fc0f iomemory:50000000-500003ff irq:17
           *-disk:0
                description: SCSI Disk
                product: WDC WD800JB-00ET
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 77.0
                serial: WD-WMAHL2892200
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 71GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2957MB
                   capacity: 2957MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2957MB
                      capabilities: nofs
           *-disk:1
                description: SCSI Disk
                product: Hitachi HDT72503
                vendor: ATA
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: V54O
                serial: VF1200R2CMK5JA
                size: 298GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   capacity: 298GB
                   capabilities: primary
           *-cdrom
                description: DVD reader
                product: COMBO LTC-48161H
                vendor: LITE-ON
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KH0G
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400-41f irq:11
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:e800-e8ff ioport:ee80-eebf iomemory:febff800-febff9ff iomemory:febff400-febff4ff irq:22
```

---

### Post by ricardisimo on 2008-04-30
(Bump)

---

### Post by ricardisimo on 2008-05-02
re-bump

---

### Post by ricardisimo on 2008-05-06
This is why I normally ask questions in "Absolute Beginners" or "General Help". Topic-specific groups rarely get me any responses at all. [sigh]...

---

