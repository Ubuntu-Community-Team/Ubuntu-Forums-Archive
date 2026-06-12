---
title: "Ubuntu 6.10 Installation On An Amd-64"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by Eli Klu on 2007-03-28
PLEASE HELP ME OUT. I REALLY WANT TO USE THE UBUNTU 6.10

I WISH TO INSTALL UBUNTU 6.10 EDGY (64 BIT) AND USE IT ALONG SIDE WITH WINDOWS XPhome (on an AMD 64BIT --SEMPRONE --DELL INSPIRON)
AM A NOVICE WHEN IT COMES LINUX, AND WINDOWS AS WELL.

AFTER RUNNING IN LIVE CD MODE AND TRING TO INSTALL UBUNTU 6.10, IT GETS TO A POINT WHERE IT CAN NOT SENSE MY HARDDISK.

I PARTITIONED THE HARDDISK(AND FORMATED THE PARTITION) IN WINDOWS BUT IT STILL DOES NOT WORK

I DONT KNOW IF IT IS THE DRIVERS FOR THE HARDDISK SUPPORTED BY UBUNTU 6.10 THAT I NEED. AND THAT IS WHAT I TRUELY NEED, WHERE DO I GET IT FROM. I HAVE SEARCHED THE DELL SUPPORT SITE, BUT FOND NOTHING

I USE A HITACHI HARDDISK

lspci:
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc Unknown device 4380
00:13.0 USB Controller: ATI Technologies Inc Unknown device 4387
00:13.1 USB Controller: ATI Technologies Inc Unknown device 4388
00:13.2 USB Controller: ATI Technologies Inc Unknown device 4389
00:13.3 USB Controller: ATI Technologies Inc Unknown device 438a
00:13.4 USB Controller: ATI Technologies Inc Unknown device 438b
00:13.5 USB Controller: ATI Technologies Inc Unknown device 4386
00:14.0 SMBus: ATI Technologies Inc Unknown device 4385 (rev 13)
00:14.1 IDE interface: ATI Technologies Inc Unknown device 438c
00:14.2 Audio device: ATI Technologies Inc Unknown device 4383
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 438d
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4384
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)

lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 894MB
     *-cpu
          product: Mobile AMD Sempron(tm) Processor 3500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni cx16 lahf_lm cr8_legacy cpufreq
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RS482 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@01:05.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:c8000000-cfffffff ioport:9000-90ff iomemory:c0100000-c010ffff irq:10
        *-pci:1
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network DISABLED
                description: Wireless interface
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@05:00.0
                logical name: eth1
                version: 01
                serial: 00:16:cf:aa:e9:e8
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:c0200000-c0203fff irq:233
        *-ide:0
             description: IDE interface
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@00:12.0
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             logical name: scsi3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=ahci
             resources: ioport:8438-843f ioport:8454-8457 ioport:8430-8437 ioport:8450-8453 ioport:8400-840f iomemory:c0004000-c00043ff irq:209
        *-usb:0
             description: USB Controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:c0005000-c0005fff irq:217
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:c0006000-c0006fff irq:225
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:c0007000-c0007fff irq:233
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:c0008000-c0008fff irq:225
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:c0009000-c0009fff irq:233
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:5
             description: USB Controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:c0004400-c00044ff irq:50
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=10 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: TD Classic 003C
                   vendor: Memorex
                   physical id: 3
                   bus info: usb@6:3
                   version: 1.00
                   serial: 05E0FB608141DA36
                   capabilities: usb-2.00 scsi
                   configuration: driver=usb-storage maxpower=200mA speed=480.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@00:14.0
             version: 13
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             resources: ioport:8410-841f iomemory:c0004800-c0004bff
        *-ide:1
             description: IDE interface
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ATIIXP_IDE
             resources: ioport:8420-842f irq:217
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-cdrom
                   product: TSSTcorp DVD+/-RW TS-L632D
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 690MB
                   capabilities: packet
        *-multimedia
             description: Audio device
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:c0000000-c0003fff irq:217
        *-isa UNCLAIMED
             description: ISA bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
        *-pci:3
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@08:00.0
                logical name: eth0
                version: 02
                serial: 00:15:c5:cb:24:c0
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 multicast=yes
                resources: iomemory:c0300000-c0301fff irq:58
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@08:01.0
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci
                resources: iomemory:c0302800-c03028ff irq:66
           *-system:1 UNCLAIMED
                description: System peripheral
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@08:01.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:c0302c00-c0302cff irq:9
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage

---

### Post by ndube on 2007-03-30
I suggest removing the partition from your hard drive and let ubuntu partition it.  Setting up a partition in windows will not allow you to install linux as windows uses NTFS and ubuntu uses EXT3.

---

### Post by jjalocha on 2007-03-31
For some reason that's still unknown to me, many people have problems with Ubuntu (Edgy) detecting their hard drive. One [solution that did it for me]("http://ubuntuforums.org/showthread.php?t=367898") was: When booting your Ubuntu CD, press F6, and add the following to your parameters:

```

pci=nomsi

```

Hope this helps in your case, too.

---

