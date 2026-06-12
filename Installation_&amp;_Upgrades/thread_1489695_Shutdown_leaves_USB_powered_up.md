---
title: "Shutdown leaves USB powered up"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by mikeiw on 2010-05-21
As a complete Linux novice, I've been installing 10.04 LTS Lucid Lynx over the last few days, and have managed to sort out most of my issues thanks to the info on this forum - for which thanks!

One issue that's causing me some inconvenience however is that when I shutdown either via the on/off button in the top right of my desktop or the *sudo shutdown -r 0* command from a terminal window, all my installed USB devices remain on despite the computer being off.

Here's a full hardware listing, as I'm a little new at Linux to know what's relevant in this case :?

```
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 4000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.7.1
          slot: Socket 939
          size: 2400MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: b
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 3c
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             width: 64 bits
        *-bank:2
             description: DIMM 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
          resources: irq:255 ioport:e400(size=32) ioport:4c00(size=64) ioport:4c40(size=64)
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:d3104000-d3104fff
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:feb00000-feb000ff
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
          resources: irq:22 ioport:dc00(size=256) ioport:e000(size=256) memory:d3103000-d3103fff
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi0
          logical name: scsi1
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-cdrom
             description: DVD writer
             product: DVD_RW ND-3500AG
             vendor: _NEC
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 2.16
             serial: [_NEC    DVD_RW ND-3500AG2.1604072300
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: ST340016A
             vendor: Seagate
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/sda
             version: 3.19
             serial: 3HS6TF56
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000bb834
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.1.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 66ac1275-d52a-4a66-ac8f-ebbe51245913
                size: 35GiB
                capacity: 35GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2010-05-16 22:26:27 filesystem=ext4 lastmountpoint=/B&#65533;&#65533;&#995;7&#65533;H&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1926;&#65533;u^ &#65533;U/&#65533;&#65533;&#1926;&#65533;~!&#65533;8&#65533;&#65533;&#65533;8&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;a modified=2010-05-18 17:14:36 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-05-20 17:11:24 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.1.0,2
                logical name: /dev/sda2
                size: 1610MiB
                capacity: 1610MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1610MiB
                   capabilities: nofs
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: scsi3
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d800(size=16) memory:d3102000-d3102fff
        *-disk
             description: ATA Disk
             product: ST3120026AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: 3.18
             serial: 3JT4690Q
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0fd50fd5
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/sdb1
                version: 3.1
                serial: 485ef1fc-ea28-9b41-ad5d-258f1bb16e0a
                size: 111GiB
                capacity: 111GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2008-05-12 19:51:44 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:c400(size=16) memory:d3101000-d3101fff
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master
          resources: memory:d3000000-d30fffff
        *-usb:0
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 6
             bus info: pci@0000:05:06.0
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=32 maxlatency=42 mingnt=1
             resources: irq:16 memory:d3000000-d3000fff
        *-usb:1
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 6.1
             bus info: pci@0000:05:06.1
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=32 maxlatency=42 mingnt=1
             resources: irq:17 memory:d3001000-d3001fff
        *-usb:2
             description: USB Controller
             product: USB 2.0
             vendor: NEC Corporation
             physical id: 6.2
             bus info: pci@0000:05:06.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=34 mingnt=16
             resources: irq:18 memory:d3002000-d30020ff
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a3
          serial: 00:17:31:b6:24:5a
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:23 memory:d3100000-d3100fff ioport:b000(size=8)
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:27 ioport:a000(size=4096) memory:d0000000-d2ffffff ioport:c0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G73 [GeForce 7300 GT]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:01:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list rom
             configuration: driver=nouveau latency=0
             resources: irq:18 memory:d0000000-d0ffffff memory:c0000000-cfffffff(prefetchable) memory:d1000000-d1ffffff ioport:a000(size=128) memory:d2000000-d201ffff(prefetchable)
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: f
          bus info: usb@1:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: CF  CardReader
             vendor: USB2.0
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
             size: 3871MiB (4059MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
                size: 3871MiB (4059MB)
                capabilities: partitioned partitioned:dos
              *-volume
                   description: Windows FAT volume
                   vendor: CanonEOS
                   physical id: 1
                   logical name: /dev/sdc1
                   logical name: /media/sdc1
                   version: FAT32
                   serial: 0000-0000
                   size: 3870MiB
                   capacity: 3871MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat label=EOS_DIGITAL mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
        *-disk:1
             description: SCSI Disk
             product: SM  CardReader
             vendor: USB2.0
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdd
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             product: SD  CardReader
             vendor: USB2.0
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sde
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             product: MS  CardReader
             vendor: USB2.0
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sdf
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdf
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:6c:52:84:a0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwpn11 driverversion=1.55+NETGEAR,09/26/2005,1.5.0.21 ip=192.168.1.6 link=yes multicast=yes wireless=IEEE 802.11g

```

Any help appreciated :)

---

