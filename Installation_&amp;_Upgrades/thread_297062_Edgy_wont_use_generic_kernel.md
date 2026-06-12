---
title: "Edgy wont use generic kernel"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by astromac on 2006-11-10
I just upgraded my dapper install to edgy.  I noticed that the 2nd cpu in my machine wasn't being utilized.  Read some folks having a similar problem and they were told to select the generic kernel in grub.  When I do that I get a kernel panic that reads 0[17179592.936000] Kernel panic - not syncing: HOST_MSG_LOOP with invalid SCB ff[17179592.936000].  I would really like to use the 2nd cpu since this is a very old system and needs all of the resources it can get.  Below is a dump of lshw.  It incorrectly reports the 2nd cpu as a PII.  Both are PIII's.

Thanks for your help.

cboerger@ubuntu-cboerger:~$ sudo lshw
Password:
ubuntu-cboerger           
    description: Mini Tower Computer
    product: HP NetServer
    vendor: Hewlett Packard
    version: E 60
    serial: US03437242
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=mini-tower frontpanel_password=unknown keyboard_password=unknown
  *-core
       description: Motherboard
       product: HP System Board
       vendor: Hewlett Packard
       physical id: 0
     *-firmware:0
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 4.06.26 PN (10/23/2000)
          size: 84KB
          capacity: 448KB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi
     *-firmware:1
          description: BIOS
          vendor: Adaptec AIC-7895
          physical id: 1
          version: 2.11.HP (06/18/1999)
          size: 224KB
          capacity: 448KB
          capabilities: pci pnp upgrade shadowing netboot
     *-cpu:0
          description: CPU
          product: Pentium III (Katmai)
          vendor: Intel Corp.
          physical id: 7
          bus info: cpu@0
          version: 6.7.3
          slot: Primary CPU
          size: 600MHz
          capacity: 700MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: e
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: internal varies unified
        *-cache:1
             description: L2 cache
             physical id: f
             slot: L2 Cache
             size: 512KB
             capacity: 512KB
             capabilities: pipeline-burst synchronous internal varies unified
     *-cpu:1
          description: CPU
          product: Pentium II
          vendor: Intel
          physical id: 8
          bus info: cpu@1
          version: 6.7.3
          slot: Secondary CPU
          size: 600MHz
          capacity: 700MHz
          clock: 100MHz
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 1GB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM0
             size: 256MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM1
             size: 256MB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: DIMM2
             size: 256MB
             width: 64 bits
        *-bank:3
             description: DIMM DRAM Synchronous
             physical id: 3
             slot: DIMM3
             size: 256MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 60000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:60000000-6fffffff
        *-pci:0
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV18 [GeForce4 MX 4000 AGP 8x]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: c1
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:e9000000-e9ffffff iomemory:f0000000-f7ffffff irq:201
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@00:04.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 4.1
             bus info: pci@00:04.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1860-186f
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-cdrom
                   description: IDE CD-ROM
                   product: HITACHI CDR-8435
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 0010
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                 *-disc
                      physical id: 0
                      logical name: /dev/hda
        *-usb:0
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 4.2
             bus info: pci@00:04.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1840-185f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 4.3
             bus info: pci@00:04.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus
             resources: irq:9
        *-scsi:0
             description: SCSI storage controller
             product: AHA-2940U/UW / AHA-39xx / AIC-7895
             vendor: Adaptec
             physical id: 5
             bus info: pci@00:05.0
             logical name: scsi0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: scsi bus_master cap_list scsi-host
             configuration: driver=aic7xxx
             resources: iomemory:e8100000-e8100fff irq:177
           *-disk:0
                description: SCSI Disk
                product: 18.2GB C 68-BX02
                vendor: HP
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BX02
                serial: 3BM0KG2P000071086R21
                size: 16GB
                capacity: 17GB
                capabilities: 5400rpm partitioned partitioned:dos
                configuration: ansiversion=2
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 16GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 737MB
                   capabilities: extended partitioned partitioned:extended
           *-disk:1
                description: SCSI Disk
                product: ST336607LW
                vendor: SEAGATE
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 0006
                serial: 3JA68AEV00007413CSR4
                size: 34GB
                capacity: 34GB
                capabilities: 10000rpm partitioned partitioned:dos
                configuration: ansiversion=3
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   capacity: 33GB
                   capabilities: primary
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   capacity: 1027MB
                   capabilities: primary nofs
           *-tape
                description: SCSI Tape
                product: DAT    9SP40-000
                vendor: SEAGATE
                physical id: 0.5.0
                bus info: scsi@0:0.5.0
                logical name: /dev/nst0
                logical name: /dev/st0
                version: 9100
                serial: HN0EB2Z
                capabilities: removable
                configuration: ansiversion=3
        *-scsi:1
             description: SCSI storage controller
             product: AHA-2940U/UW / AHA-39xx / AIC-7895
             vendor: Adaptec
             physical id: 5.1
             bus info: pci@00:05.1
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: scsi bus_master cap_list scsi-host
             configuration: driver=aic7xxx
             resources: iomemory:e8101000-e8101fff irq:177
        *-network
             description: Ethernet interface
             product: 82557/8/9 [Ethernet Pro 100]
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@00:06.0
             logical name: eth0
             version: 08
             serial: 00:e0:18:c3:47:45
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=full firmware=N/A ip=192.168.101.124 link=yes multicast=yes port=MII speed=100MB/s
             resources: iomemory:e8102000-e8102fff ioport:1800-183f iomemory:e8000000-e80fffff irq:185
        *-usb:1
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 9
             bus info: pci@00:09.0
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:e8103000-e8103fff irq:193
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-386 ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb
                   description: USB hub
                   product: TUSB2046 Hub
                   vendor: Texas Instruments, Inc.
                   physical id: 3
                   bus info: usb@2:3
                   version: 1.25
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
                 *-usb
                      description: Mouse
                      product: Apple Optical USB Mouse
                      vendor: Mitsumi Electric
                      physical id: 2
                      bus info: usb@2:3.2
                      version: 1.08
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 9.1
             bus info: pci@00:09.1
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:e8104000-e8104fff irq:177
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-386 ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: NEC Corporation
             physical id: 9.2
             bus info: pci@00:09.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:e8105000-e81050ff irq:185
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-386 ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=5 speed=480.0MB/s
        *-pci:1
             description: PCI bridge
             product: DECchip 21152
             vendor: Digital Equipment Corporation
             physical id: c
             bus info: pci@00:0c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
cboerger@ubuntu-cboerger:~$

---

