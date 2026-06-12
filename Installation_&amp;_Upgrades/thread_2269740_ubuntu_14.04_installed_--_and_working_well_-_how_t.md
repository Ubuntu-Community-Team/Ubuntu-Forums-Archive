---
title: "ubuntu 14.04 installed -- and working well - how to add windows 8   on UEFI system"
date: 2015-03-17
forum: Installation &amp; Upgrades
---

### Post by xigen on 2015-03-17
I got rocksmith 2014 as a present.  

Play on Linux --> waaaay too much delay 
Virtualization -->  too much delay

How do I install windows 8 on my Ubuntu system with UEFI? 




Ubuntu 14.04
Motherboard: 970A-UD3P Gigabyte Technology Co., Ltd.
CPU: AMD FX(tm)-8320 Eight-Core Processor

 #lshw

```

           description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: Dimm0_PartNum
             vendor: Dimm0_Manufacturer
             physical id: 0
             serial: Dimm0_SerNum
             slot: Node0_Dimm0
        *-bank:1
             description: DIMM Synchronous [empty]
             product: Dimm1_PartNum
             vendor: Dimm1_Manufacturer
             physical id: 1
             serial: Dimm1_SerNum
             slot: Node0_Dimm1
        *-bank:2
             description: DIMM Synchronous [empty]
             product: Dimm2_PartNum
             vendor: Dimm2_Manufacturer
             physical id: 2
             serial: Dimm2_SerNum
             slot: Node0_Dimm2
        *-bank:3
             description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
             product: BLS8G3D1339DS
             vendor: Undefined
             physical id: 3
             serial: A3136436
             slot: Node0_Dimm3
             size: 8GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci:0
          description: Host bridge
          product: RD890 PCI to PCI bridge (external gfx0 port B)
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port D)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:52 memory:fe300000-fe3fffff
           *-usb
                description: USB controller
                product: VIA Technologies, Inc.
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:72 memory:fe300000-fe300fff
        *-pci:1
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port F)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:53 ioport:e000(size=4096) memory:fe200000-fe2fffff ioport:d2200000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 06
                serial: e8:de:27:06:86:10
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.038.00-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair
                resources: irq:73 ioport:e000(size=256) memory:fe200000-fe200fff memory:d2200000-d2203fff
        *-pci:2
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port H)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:53 ioport:d000(size=4096) memory:fe100000-fe1fffff ioport:d2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 06
                serial: 74:d4:35:5e:c7:63
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.038.00-NAPI duplex=full ip=192.168.2.139 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:74 ioport:d000(size=256) memory:fe100000-fe100fff memory:d2100000-d2103fff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=16) memory:fe407000-fe4073ff
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fe406000-fe406fff
        *-usb:1
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:fe405000-fe4050ff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fe404000-fe404fff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:fe403000-fe4030ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=32
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
             resources: ioport:c000(size=4096)
           *-multimedia
                description: Multimedia audio controller
                product: ICE1712 [Envy24] PCI Multi-Channel I/O Controller
                vendor: VIA Technologies Inc.
                physical id: 6
                bus info: pci@0000:04:06.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=snd_ice1712 latency=32
                resources: irq:20 ioport:c040(size=32) ioport:c070(size=16) ioport:c060(size=16) ioport:c000(size=64)
        *-usb:4
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fe402000-fe402fff
        *-pci:4
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:b000(size=4096) memory:fd000000-fe0fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GK107 [GeForce GTX 650]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:75 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:b000(size=128) memory:fe000000-fe07ffff
           *-multimedia
                description: Audio device
                product: GK107 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:fe080000-fe083fff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fe401000-fe401fff
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:fe400000-fe4000ff
     *-pci:1
          description: Host bridge
          product: Family 15h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 15h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: INTEL SSDSC2BW24
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: DC32
             serial: CVDA401101S52403GN
             size: 223GiB (240GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=eaf7ff9e-a858-4264-abc5-36985fe65e9d sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: 006e-e1a5
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:1
                description: EFI partition
                vendor: Linux
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot
                version: 1.0
                serial: 8f45ec5b-72a0-417e-85c8-14638414cd12
                size: 244MiB
                capabilities: extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2014-08-25 09:15:29 mount.fstype=ext2 mount.options=rw,relatime mounted=2014-08-25 09:15:29 state=mounted
           *-volume:2
                description: LVM Physical Volume
                vendor: Linux
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sda3
                serial: mqaITd-GLUd-DYwr-R4HT-3Pv2-amfJ-tIBFdq
                size: 222GiB
                capabilities: multi lvm2
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DRW-24B1ST   i
             vendor: ASUS
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@8:1.1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: sectorsize=512 signature=0002a926
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/meow/littlemeow
                version: 1.0
                serial: 9bc91839-1552-450b-8779-09609d8f0dc9
                size: 230GiB
                capacity: 230GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-07-08 19:22:41 filesystem=ext4 label=littlemeow lastmountpoint=/media/meow/littlemeow modified=2014-08-25 09:16:40 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2014-08-25 09:16:40 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@6:0.0.0,2
                logical name: /dev/sdb2
                size: 2045MiB
                capacity: 2045MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 2045MiB
                   capabilities: nofs

```

---

### Post by oldfred on 2015-03-18
Just be sure to boot Windows installer in UEFI mode. If you happen to boot in BIOS mode it converts drive to MBR(msdos) effectively erasing it.

You still have to make sure to have fast boot off. And depending on your model computer may only boot Windows and need work arounds to enable boot to grub menu,

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
If issues you may need these?
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 
powercfg /h off

Best to fully backup efi partition and Ubuntu first.

If you partition in advance be sure to create the extra partition(s) Windows needs. You only have one efi partition and Windows & Ubuntu/grub share that.


 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

