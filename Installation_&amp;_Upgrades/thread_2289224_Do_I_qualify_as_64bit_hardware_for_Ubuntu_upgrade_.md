---
title: "Do I qualify as 64bit hardware for Ubuntu upgrade and... best way to do it if so?"
date: 2015-08-02
forum: Installation &amp; Upgrades
---

### Post by ButchMel on 2015-08-02
I have the following system information (below) and I was wondering if this means I qualify as a ''64bit'' hardware so I could upgrade to latest Ubuntu version safely?

Also, as I essentially use it as a server with multiple hard drives connected to this machine, and considering I'm far from an expert, should I proceed with an upgrade on top of this version and expect to keep all my current settings, profiles, accesses, or should I wipe everything and reinstall fresh ?

Would this newer version be easier than 12.xxx ?

```

 slot: System board or motherboard
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: 64D64320GU5C
             vendor: JEDEC ID:C1 00 00 00 00 00 00 00
             physical id: 0
             serial: 24FE0808
             slot: XMM1
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: K
             vendor: JEDEC ID:7F 98 00 00 00 00 00 00
             physical id: 1
             serial: 20321E72
             slot: XMM2
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: 64D64320GU5C
             vendor: JEDEC ID:C1 00 00 00 00 00 00 00
             physical id: 2
             serial: 26FE0808
             slot: XMM3
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: M3 68L6423FTN-CCC
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 3
             serial: FEAE06F3
             slot: XMM4
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 34
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 512KiB
             width: 4 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-cpu:1
          product: Intel(R) Pentium(R) 4 CPU 3.40GHz
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@1
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          size: 3400MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
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
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:cfe00000-cfe7ffff ioport:3800(size=8) memory:e0000000-efffffff memory:cff00000-cff3ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82915G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:cfe80000-cfefffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:80000000-801fffff ioport:80200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:7000(size=4096) memory:f0200000-f04fffff ioport:80400000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:40:00.0
                logical name: eth0
                version: 01
                serial: 00:12:79:ad:4c:71
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 duplex=full firmware=5751-v3.29a ip=10.169.205.137 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:17 memory:f0400000-f040ffff
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:3440(size=32)
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:3460(size=32)
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:3480(size=32)
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:34a0(size=32)
        *-usb:4
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:cff40000-cff403ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:1000(size=4096) memory:f0500000-f07fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 46
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=32
                resources: irq:16 memory:f0500000-f05007ff ioport:1000(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:21 ioport:3000(size=256) ioport:3400(size=64) memory:cff40400-cff405ff memory:cff40600-cff406ff
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:34e0(size=16)
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:3818(size=8) ioport:3830(size=4) ioport:3820(size=8) ioport:3834(size=4) ioport:34f0(size=16)
     *-scsi:0
          physical id: 4
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: COMBO SOHC-4836K
             vendor: LITE-ON
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: SQK5
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 6
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD800JD-60LS
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 10.0
             serial: WD-WMAM9DY76307
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000e9fcc
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: a8d8094b-40b8-41fa-a177-a43a4e485c9a
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable ext2 initialized
                configuration: filesystem=ext2 modified=2015-02-22 14:59:08 mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 74GiB
                capacity: 74GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: Axt1M6-eoSs-F7RL-O4Y9-AOen-hNPc-yCkVnN
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: multi lvm2
     *-scsi:2
          physical id: 7
          logical name: scsi3
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: WDC WD10EALX-009
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: 15.0
             serial: WD-WCATR9929152
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=eae9456b
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/WDblue1
                version: 3.1
                serial: c43b-98bb
                size: 931GiB
                capacity: 931GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2012-03-30 21:54:37 filesystem=ntfs label=WDblue1 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
        *-disk:1
             description: ATA Disk
             product: ST3160815AS
             vendor: Seagate
             physical id: 0.1.0
             bus info: scsi@3:0.1.0
             logical name: /dev/sdc
             version: 3.AA
             serial: 5RA0N9WL
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=c42d3ee5
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.1.0,1
                logical name: /dev/sdc1
                logical name: /media/OLDWinVista
                version: 3.1
                serial: 62adac7a-09db-314f-ab42-db2a9706365a
                size: 58GiB
                capacity: 58GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2011-01-06 16:26:50 filesystem=ntfs label=OLDWinVista mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@3:0.1.0,2
                logical name: /dev/sdc2
                logical name: /media/SONARData2
                version: 3.1
                serial: f2ae51b2-d27e-6d44-aa1d-c3f5e96aa914
                size: 90GiB
                capacity: 90GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2007-07-11 23:31:34 filesystem=ntfs label=SONARData2 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
     *-scsi:3
          physical id: 8
          bus info: usb@1:4
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdf
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=91ca97ec
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@7:0.0.0,1
                logical name: /dev/sdf1
                logical name: /media/eSATA-Crab_
                version: 3.1
                serial: 7076-442f
                size: 232GiB
                capacity: 232GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-10-17 00:00:45 filesystem=ntfs label=eSATA-Crab modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
     *-scsi:4
          physical id: 9
          logical name: scsi5
        *-disk
             description: SCSI Disk
             product: My Book
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sde
             version: 1028
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=8d399bc0
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sde1
                logical name: /media/Backup_WD_MyBook
                version: 3.1
                serial: aac814f3-87ec-3542-8292-2d351de3cbf6
                size: 488GiB
                capacity: 488GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2009-06-10 21:19:01 filesystem=ntfs label=Backup_WD_MyBook mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@5:0.0.0,2
                logical name: /dev/sde2
                logical name: /media/NetAccess_WD_MyBook
                version: 3.1
                serial: 34c87c76-a97a-214d-8975-4edcbf04e9eb
                size: 443GiB
                capacity: 443GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2009-06-10 21:20:25 filesystem=ntfs label=NetAccess_WD_MyBook mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
     *-scsi:5
          physical id: a
          logical name: scsi6
        *-enclosure UNCLAIMED
             description: SCSI Enclosure
             product: My Book Device
             vendor: WD
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             configuration: ansiversion=4
robert@CrabConnect:~$ 

```

---

### Post by howefield on 2015-08-02
Looks like you have a cpu capable of 32 bits, but not 64.

Doesn't mean you can't upgrade, just means you stick to 32 bit.

---

### Post by ButchMel on 2015-08-02
Yes but.... Latest version is 64bit only, no?

---

### Post by howefield on 2015-08-02
Ubuntu desktop and server is available in both 32 and 64 bit

---

