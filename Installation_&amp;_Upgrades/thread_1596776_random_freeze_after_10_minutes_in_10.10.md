---
title: "random freeze after 10 minutes in 10.10"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by olgita on 2010-10-14
[COLOR=Purple]Hello, I am a Ubuntu **user** since a few years (Breezy Badger was my first) now but I still don't know much about computers or commands so please bear with me. I used 10.04 on my HP pavillion  PC of two years old without any problems. Now I upgraded to 10.10 with update manager. And it boots fine, but whatever I do, after aprox. 10 minutes everything just freezes. And I don't remember the magic phrase for soft reset, so I hit the power button. I have searched the forums and could not find a satisfactory answer to my problem. I found this thread [http://ubuntuforums.org/showthread.php?t=1585973](http://ubuntuforums.org/showthread.php?t=1585973) but have no idea how to do what's requested. Could anyone please tell me what to do?
I know how to open a terminal, and type a command or two but that's basically it. Please be patient with me. 
Thank you.[/COLOR]

---

### Post by Martyn Collins, Esq. on 2010-10-14
I am having the exact same problem. Persistently at this point.  I am totally patient, even though I should not be.

---

### Post by olgita on 2010-10-15
[FONT="Comic Sans MS"][SIZE="2"]I would really like some help with this problem because I can't rely on my system and that is very annoying!!!:confused::mad:
so in case anyone is interested hereafter are the outputs to dmesg, lshw, lspci,lspci | grep VGA.
olga@olga-laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
olga@olga-laptop:~$ 

olga@olga-laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
olga@olga-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
09:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
0b:00.0 Multimedia controller: Philips Semiconductors SAA7160 (rev 03)
olga@olga-laptop:~$ 

             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: Hewlett-Packard Company
             vendor: Hewlett-Packard Company
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:7000(size=4096) memory:d2500000-d26fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Radeon HD 3200 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:48 memory:c0000000-cfffffff ioport:7000(size=256) memory:d2600000-d260ffff memory:d2500000-d25fffff
           *-multimedia
                description: Audio device
                product: RS780 Azalia controller
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:47 memory:d2610000-d2613fff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=16384) memory:d1500000-d24fffff ioport:d0000000(size=16777216)
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:d1400000-d14fffff ioport:d2800000(size=1048576)
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:d1400300-d14003ff memory:d2800000-d280ffff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:08:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:d1400200-d14002ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:08:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:17 memory:d1400100-d14001ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.4
                bus info: pci@0000:08:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
                resources: memory:d1400000-d14000ff
        *-pci:3
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 memory:d1300000-d13fffff ioport:d1000000(size=1048576)
           *-network
                description: Wireless interface
                product: BCM4321 802.11a/b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth1
                version: 03
                serial: 00:1a:73:e5:35:d6
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.38 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:18 memory:d1300000-d1303fff memory:d1000000-d10fffff
        *-pci:4
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:2000(size=4096) memory:d2900000-d29fffff ioport:d1100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0a:00.0
                logical name: eth0
                version: 02
                serial: 00:1b:38:ff:82:24
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:45 ioport:2000(size=256) memory:d1110000-d1110fff memory:d1100000-d110ffff memory:d1120000-d112ffff
        *-pci:5
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 5)
             vendor: Advanced Micro Devices [AMD]
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 memory:d1200000-d12fffff
           *-multimedia UNCLAIMED
                description: Multimedia controller
                product: SAA7160
                vendor: Philips Semiconductors
                physical id: 0
                bus info: pci@0000:0b:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: msi pciexpress pm bus_master cap_list
                configuration: latency=0
                resources: memory:d1200000-d12fffff
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi2
             logical name: scsi3
             logical name: scsi5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:46 ioport:8038(size=8) ioport:804c(size=4) ioport:8030(size=8) ioport:8048(size=4) ioport:8010(size=16) memory:d2708000-d27083ff
           *-disk:0
                description: ATA Disk
                product: FUJITSU MHZ2250B
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 8909
                serial: K617T82255DW
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=7d612573
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: e042d954-2916-4038-ba36-c873630d6b7e
                   size: 224GiB
                   capacity: 224GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-04-28 09:49:12 filesystem=ext4 lastmountpoint=/&#1238;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;x&#65533;&#65533;p/&#65533;P^&#65533;&#65533;&#65533;l!&#65533;x&#65533;&#65533;@^&#65533;&#65533; &#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;A&#65533;h^&#65533;&#65533;yo!&#65533;&#65533;d modified=2010-10-13 22:02:28 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-10-14 19:01:30 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 8110MiB
                   capacity: 8110MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 8110MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: Hitachi HTS54252
                vendor: Hitachi
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: BBFO
                serial: 071017BB0F00WDGGUHPC
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0000ef00
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: e687d4b3-c787-4079-b3c7-74cb26c75c04
                   size: 224GiB
                   capacity: 224GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-08-24 21:35:19 filesystem=ext4 label=New Volume lastmountpoint=/media/New Volume&#65533;O&#365;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;F&#65533;>&#58654;&#65533;&#65533;h &#65533;H&#65533;~&#65533;&#65533;&#65533;&#65533;&#65533;H&#65533;~&#65533; &#65533;~&#65533; modified=2010-10-14 01:42:55 mounted=2010-10-14 01:27:44 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdb2
                   size: 8110MiB
                   capacity: 8110MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 8110MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L633L
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@5:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0400
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:d2707000-d2707fff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:d2706000-d2706fff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:d2708500-d27085ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d2705000-d2705fff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d2704000-d2704fff
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:d2708400-d27084ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8000(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:d2700000-d2703fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:6
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:1000(size=4096)
     *-pci:1
          description: Host bridge
          product: Family 11h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 11h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 11h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 11h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
olga@olga-laptop:~$ 

[    0.486748]   alloc kstat_irqs on node -1
[    0.486753] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.486757] pci 0000:00:04.0: setting latency timer to 64
[    0.486764]   alloc irq_desc for 17 on node -1
[    0.486766]   alloc kstat_irqs on node -1
[    0.486770] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.486774] pci 0000:00:05.0: setting latency timer to 64
[    0.486781]   alloc irq_desc for 18 on node -1
[    0.486783]   alloc kstat_irqs on node -1
[    0.486787] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.486791] pci 0000:00:06.0: setting latency timer to 64
[    0.486797]   alloc irq_desc for 19 on node -1
[    0.486799]   alloc kstat_irqs on node -1
[    0.486803] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.486807] pci 0000:00:07.0: setting latency timer to 64
[    0.486815] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.486818] pci 0000:00:0a.0: setting latency timer to 64
[    0.486828] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.486831] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.486833] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.486836] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.486839] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.486842] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.486845] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.486847] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.486850] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.486853] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.486856] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.486859] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.486861] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.486864] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.486867] pci_bus 0000:00: resource 18 [mem 0xc0000000-0xdfffffff]
[    0.486870] pci_bus 0000:00: resource 19 [mem 0xe4000000-0xffffffff]
[    0.486873] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
[    0.486876] pci_bus 0000:01: resource 1 [mem 0xd2500000-0xd26fffff]
[    0.486879] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.486882] pci_bus 0000:02: resource 0 [io  0x3000-0x6fff]
[    0.486884] pci_bus 0000:02: resource 1 [mem 0xd1500000-0xd24fffff]
[    0.486887] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
[    0.486890] pci_bus 0000:08: resource 1 [mem 0xd1400000-0xd14fffff]
[    0.486893] pci_bus 0000:08: resource 2 [mem 0xd2800000-0xd28fffff pref]
[    0.486896] pci_bus 0000:09: resource 1 [mem 0xd1300000-0xd13fffff]
[    0.486899] pci_bus 0000:09: resource 2 [mem 0xd1000000-0xd10fffff 64bit pref]
[    0.486902] pci_bus 0000:0a: resource 0 [io  0x2000-0x2fff]
[    0.486905] pci_bus 0000:0a: resource 1 [mem 0xd2900000-0xd29fffff]
[    0.486908] pci_bus 0000:0a: resource 2 [mem 0xd1100000-0xd11fffff 64bit pref]
[    0.486911] pci_bus 0000:0b: resource 1 [mem 0xd1200000-0xd12fffff]
[    0.486914] pci_bus 0000:80: resource 0 [io  0x1000-0x1fff]
[    0.486916] pci_bus 0000:80: resource 4 [io  0x0000-0x0cf7]
[    0.486919] pci_bus 0000:80: resource 5 [io  0x0d00-0xffff]
[    0.486922] pci_bus 0000:80: resource 6 [mem 0x000a0000-0x000bffff]
[    0.486925] pci_bus 0000:80: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.486927] pci_bus 0000:80: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.486930] pci_bus 0000:80: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.486933] pci_bus 0000:80: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.486936] pci_bus 0000:80: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.486939] pci_bus 0000:80: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.486941] pci_bus 0000:80: resource 13 [mem 0x000dc000-0x000dffff]
[    0.486944] pci_bus 0000:80: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.486947] pci_bus 0000:80: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.486950] pci_bus 0000:80: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.486953] pci_bus 0000:80: resource 17 [mem 0x000ec000-0x000effff]
[    0.486955] pci_bus 0000:80: resource 18 [mem 0xc0000000-0xdfffffff]
[    0.486958] pci_bus 0000:80: resource 19 [mem 0xe4000000-0xffffffff]
[    0.487003] NET: Registered protocol family 2
[    0.487077] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.487369] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.487974] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.488285] TCP: Hash tables configured (established 131072 bind 65536)
[    0.488288] TCP reno registered
[    0.488292] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.488305] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.488412] NET: Registered protocol family 1
[    2.088157] pci 0000:00:12.2: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    3.688156] pci 0000:00:13.2: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    3.688194] pci 0000:01:05.0: Boot video device
[    3.688223] PCI: CLS 64 bytes, default 64
[    3.688286] Simple Boot Flag value 0x33 read from CMOS RAM was invalid
[    3.688289] Simple Boot Flag at 0x0 set to 0x1
[    3.688634] cpufreq-nforce2: No nForce2 chipset.
[    3.688667] Scanning for low memory corruption every 60 seconds
[    3.688824] audit: initializing netlink socket (disabled)
[    3.688836] type=2000 audit(1286969792.688:1): initialized
[    3.701138] highmem bounce pool size: 64 pages
[    3.701144] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.705169] VFS: Disk quotas dquot_6.5.2
[    3.705233] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.706803] fuse init (API version 7.14)
[    3.706914] msgmni has been set to 1684
[    3.716138] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.716141] io scheduler noop registered
[    3.716144] io scheduler deadline registered
[    3.716159] io scheduler cfq registered (default)
[    3.716315] pcieport 0000:00:04.0: setting latency timer to 64
[    3.716348]   alloc irq_desc for 40 on node -1
[    3.716350]   alloc kstat_irqs on node -1
[    3.716391] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    3.716476] pcieport 0000:00:05.0: setting latency timer to 64
[    3.716563]   alloc irq_desc for 41 on node -1
[    3.716565]   alloc kstat_irqs on node -1
[    3.716572] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    3.716635] pcieport 0000:00:06.0: setting latency timer to 64
[    3.716662]   alloc irq_desc for 42 on node -1
[    3.716664]   alloc kstat_irqs on node -1
[    3.716670] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
[    3.716735] pcieport 0000:00:07.0: setting latency timer to 64
[    3.716762]   alloc irq_desc for 43 on node -1
[    3.716764]   alloc kstat_irqs on node -1
[    3.716770] pcieport 0000:00:07.0: irq 43 for MSI/MSI-X
[    3.716831] pcieport 0000:00:0a.0: setting latency timer to 64
[    3.716858]   alloc irq_desc for 44 on node -1
[    3.716860]   alloc kstat_irqs on node -1
[    3.716866] pcieport 0000:00:0a.0: irq 44 for MSI/MSI-X
[    3.716957] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.716978] Firmware did not grant requested _OSC control
[    3.717003] Firmware did not grant requested _OSC control
[    3.717013] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.717301] ACPI: AC Adapter [ACAD] (on-line)
[    3.717365] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    3.717372] ACPI: Power Button [PWRB]
[    3.717433] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    3.717583] ACPI: Lid Switch [LID]
[    3.717629] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    3.717633] ACPI: Power Button [PWRF]
[    3.718014] ACPI: acpi_idle registered with cpuidle
[    3.821720] thermal LNXTHERM:01: registered as thermal_zone0
[    3.821728] ACPI: Thermal Zone [TZ01] (39 C)
[    3.821810] ERST: Table is not found!
[    3.822036] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.822798] isapnp: Scanning for PnP cards...
[    3.823578] brd: module loaded
[    3.824123] loop: module loaded
[    3.824356] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.824396] pata_acpi 0000:00:14.1: setting latency timer to 64
[    3.824790] Fixed MDIO Bus: probed
[    3.824828] PPP generic driver version 2.4.2
[    3.824865] tun: Universal TUN/TAP device driver, 1.6
[    3.824867] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.824950] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.825003] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.825026] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    3.825030] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    3.825066] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    3.825137] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    3.825152] ehci_hcd 0000:00:12.2: debug port 1
[    3.825182] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd2708500
[    3.836626] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    3.836758] hub 1-0:1.0: USB hub found
[    3.836764] hub 1-0:1.0: 6 ports detected
[    3.836885] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.836897] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    3.836901] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.836934] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    3.836953] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    3.836968] ehci_hcd 0000:00:13.2: debug port 1
[    3.836992] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd2708400
[    3.848662] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    3.848772] hub 2-0:1.0: USB hub found
[    3.848776] hub 2-0:1.0: 6 ports detected
[    3.848853] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.848900] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.848911] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    3.848915] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    3.848954] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    3.849018] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd2707000
[    3.910735] hub 3-0:1.0: USB hub found
[    3.910777] hub 3-0:1.0: 3 ports detected
[    3.910840] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.910851] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    3.910855] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    3.910897] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    3.910950] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd2706000
[    3.970700] hub 4-0:1.0: USB hub found
[    3.970707] hub 4-0:1.0: 3 ports detected
[    3.970769] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.970780] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    3.970784] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.970820] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    3.970886] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd2705000
[    3.984789] ACPI: Battery Slot [BAT0] (battery present)
[    4.030684] hub 5-0:1.0: USB hub found
[    4.030691] hub 5-0:1.0: 3 ports detected
[    4.030753] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.030764] ohci_hcd 0000:00:13.1: setting latency timer to 64
[    4.030768] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    4.030804] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    4.030863] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd2704000
[    4.090706] hub 6-0:1.0: USB hub found
[    4.090746] hub 6-0:1.0: 3 ports detected
[    4.090816] uhci_hcd: USB Universal Host Controller Interface driver
[    4.090900] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    4.130933] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.130949] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.131063] mice: PS/2 mouse device common for all mice
[    4.133598] rtc_cmos 00:04: RTC can wake from S4
[    4.133637] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    4.133664] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    4.133773] device-mapper: uevent: version 1.0.3
[    4.133920] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    4.134032] device-mapper: multipath: version 1.1.1 loaded
[    4.134035] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.134188] EISA: Probing bus 0 at eisa.0
[    4.134191] EISA: Cannot allocate resource for mainboard
[    4.134194] Cannot allocate resource for EISA slot 1
[    4.134196] Cannot allocate resource for EISA slot 2
[    4.134199] Cannot allocate resource for EISA slot 3
[    4.134201] Cannot allocate resource for EISA slot 4
[    4.134204] Cannot allocate resource for EISA slot 5
[    4.134206] Cannot allocate resource for EISA slot 6
[    4.134209] Cannot allocate resource for EISA slot 7
[    4.134211] Cannot allocate resource for EISA slot 8
[    4.134213] EISA: Detected 0 cards.
[    4.134328] cpuidle: using governor ladder
[    4.134330] cpuidle: using governor menu
[    4.134642] TCP cubic registered
[    4.134774] NET: Registered protocol family 10
[    4.135209] lo: Disabled Privacy Extensions
[    4.135487] NET: Registered protocol family 17
[    4.135517] powernow-k8: Found 1 AMD Turion(tm) Ultra Dual-Core Mobile ZM-80 (2 cpu cores) (version 2.20.00)
[    4.135564] powernow-k8:    0 : pstate 0 (2100 MHz)
[    4.135567] powernow-k8:    1 : pstate 2 (1050 MHz)
[    4.135569] powernow-k8:    2 : pstate 1 (800 MHz)
[    4.135571] powernow-k8:    3 : pstate 3 (525 MHz)
[    4.171475] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.176671] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    4.205236] isapnp: No Plug & Play device found
[    4.205587] Using IPI No-Shortcut mode
[    4.205675] PM: Resume from disk failed.
[    4.205689] registered taskstats version 1
[    4.206157]   Magic number: 14:746:630
[    4.206439] rtc_cmos 00:04: setting system clock to 2010-10-13 11:36:02 UTC (1286969762)
[    4.206443] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.206445] EDD information not available.
[    4.207701] Freeing unused kernel memory: 684k freed
[    4.208790] Write protecting the kernel text: 4932k
[    4.209220] Write protecting the kernel read-only data: 1976k
[    4.248929] udev[76]: starting version 163
[    4.337345] sdhci: Secure Digital Host Controller Interface driver
[    4.337349] sdhci: Copyright(c) Pierre Ossman
[    4.338788] sdhci-pci 0000:08:00.0: SDHCI controller found [197b:2382] (rev 0)
[    4.338814] sdhci-pci 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.338861] sdhci-pci 0000:08:00.0: setting latency timer to 64
[    4.338905] Registered led device: mmc0::
[    4.380984] mmc0: SDHCI controller on PCI [0000:08:00.0] using ADMA
[    4.381008] sdhci-pci 0000:08:00.2: SDHCI controller found [197b:2381] (rev 0)
[    4.381033] sdhci-pci 0000:08:00.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.381046] sdhci-pci 0000:08:00.2: Refusing to bind to secondary interface.
[    4.381052] sdhci-pci 0000:08:00.2: PCI INT A disabled
[    4.392176] ahci 0000:00:11.0: version 3.0
[    4.392232]   alloc irq_desc for 22 on node -1
[    4.392235]   alloc kstat_irqs on node -1
[    4.392244] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.392302]   alloc irq_desc for 45 on node -1
[    4.392304]   alloc kstat_irqs on node -1
[    4.392316] ahci 0000:00:11.0: irq 45 for MSI/MSI-X
[    4.392546] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    4.392551] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio ccc 
[    4.417319] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.417370] r8169 0000:0a:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.417430] r8169 0000:0a:00.0: setting latency timer to 64
[    4.417470]   alloc irq_desc for 46 on node -1
[    4.417472]   alloc kstat_irqs on node -1
[    4.417492] r8169 0000:0a:00.0: irq 46 for MSI/MSI-X
[    4.418050] r8169 0000:0a:00.0: eth0: RTL8102e at 0xf80ea000, 00:1b:38:ff:82:24, XID 04900000 IRQ 46
[    4.437201] scsi0 : ahci
[    4.437453] scsi1 : ahci
[    4.437595] scsi2 : ahci
[    4.437738] scsi3 : ahci
[    4.437875] scsi4 : ahci
[    4.438011] scsi5 : ahci
[    4.438231] ata1: SATA max UDMA/133 abar m1024@0xd2708000 port 0xd2708100 irq 45
[    4.438236] ata2: SATA max UDMA/133 abar m1024@0xd2708000 port 0xd2708180 irq 45
[    4.438241] ata3: SATA max UDMA/133 abar m1024@0xd2708000 port 0xd2708200 irq 45
[    4.438245] ata4: SATA max UDMA/133 abar m1024@0xd2708000 port 0xd2708280 irq 45
[    4.438249] ata5: SATA max UDMA/133 abar m1024@0xd2708000 port 0xd2708300 irq 45
[    4.438253] ata6: SATA max UDMA/133 abar m1024@0xd2708000 port 0xd2708380 irq 45
[    4.438564] scsi6 : pata_atiixp
[    4.438690] scsi7 : pata_atiixp
[    4.439861] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8000 irq 14
[    4.439865] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8008 irq 15
[    4.692162] usb 5-1: new full speed USB device using ohci_hcd and address 2
[    4.756218] ata6: SATA link down (SStatus 0 SControl 300)
[    4.756247] ata5: SATA link down (SStatus 0 SControl 300)
[    4.756274] ata3: SATA link down (SStatus 0 SControl 300)
[    4.920633] ata4: softreset failed (device not ready)
[    4.920639] ata4: applying SB600 PMP SRST workaround and retrying
[    4.920658] ata1: softreset failed (device not ready)
[    4.920661] ata1: applying SB600 PMP SRST workaround and retrying
[    4.920678] ata2: softreset failed (device not ready)
[    4.920681] ata2: applying SB600 PMP SRST workaround and retrying
[    5.084169] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.084204] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.084224] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.085116] ata2.00: ATA-8: Hitachi HTS542525K9SA00, BBFOC32P, max UDMA/100
[    5.085119] ata2.00: 488397168 sectors, multi 16: LBA48 
[    5.085145] ata1.00: ATA-8: FUJITSU MHZ2250BH G2, 8909, max UDMA/100
[    5.085148] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    5.086505] ata2.00: configured for UDMA/100
[    5.086530] ata1.00: configured for UDMA/100
[    5.098431] ata4.00: ATAPI: TSSTcorp CDDVDW TS-L633L, 0400, max UDMA/100
[    5.101604] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2250B 8909 PQ: 0 ANSI: 5
[    5.101794] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.101946] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
[    5.102069] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    5.102150] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    5.102154] sd 1:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    5.102217] sd 1:0:0:0: [sdb] Write Protect is off
[    5.102221] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.102225] sd 0:0:0:0: [sda] Write Protect is off
[    5.102230] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.102256] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.102259] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.102494]  sdb:
[    5.102566]  sda:
[    5.115082] ata4.00: configured for UDMA/100
[    5.136525] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633L  0400 PQ: 0 ANSI: 5
[    5.152742] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.152746] Uniform CD-ROM driver Revision: 3.20
[    5.152852] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    5.152908] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    5.181785]  sda1 sda2 < sda5 >
[    5.213161] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.425056]  sdb1 sdb2 < sdb5 >
[    5.458576] sd 1:0:0:0: [sdb] Attached SCSI disk
[    5.676304] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    5.676310] EXT4-fs (sda1): write access will be enabled during recovery
[    7.598120] EXT4-fs (sda1): recovery complete
[    7.599239] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   32.592398] udev[413]: starting version 163
[   32.648408] lp: driver loaded but no devices found
[   32.694367] lirc_dev: IR Remote Control driver registered, major 251 
[   32.694519] lirc_ene0100: module is from the staging directory, the quality is unknown, you have been warned.
[   32.695269] enecir 00:0a: lirc_dev: driver enecir registered at minor = 0
[   32.695367] enecir: KB3926C detected, driver support is not complete!
[   32.695370] enecir: chip is 0x3926 - 0x00, 0xc0
[   32.695378] enecir: hardware features:
[   32.695380] enecir: learning and tx off, gpio40_learn off, fan_in off
[   32.695382] enecir: driver has been succesfully loaded
[   32.700001] Adding 8305568k swap on /dev/sda5.  Priority:-1 extents:1 across:8305568k 
[   32.724796] lis3lv02d: laptop model unknown, using default axes configuration
[   32.725559] lis3lv02d: 8 bits sensor found
[   32.786086] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   32.786508] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.832488] lib80211: common routines for IEEE802.11 drivers
[   32.832494] lib80211_crypt: registered algorithm 'NULL'
[   32.903932] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   32.913459] jmb38x_ms 0000:08:00.3: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   32.913468] jmb38x_ms 0000:08:00.3: setting latency timer to 64
[   32.927766] acpi device:02: registered as cooling_device2
[   32.928005] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input4
[   32.928071] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   32.949258] wl: module license 'MIXED/Proprietary' taints kernel.
[   32.949264] Disabling lock debugging due to kernel taint
[   32.964675] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input5
[   32.984208] Linux agpgart interface v0.103
[   33.011622] Registered led device: hp::hddprotect
[   33.011646] lis3lv02d driver loaded.
[   33.053611] wl 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   33.053620] wl 0000:09:00.0: setting latency timer to 64
[   33.118297] type=1400 audit(1286969791.406:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=717 comm="apparmor_parser"
[   33.118598] type=1400 audit(1286969791.406:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=717 comm="apparmor_parser"
[   33.118773] type=1400 audit(1286969791.406:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=717 comm="apparmor_parser"
[   33.122247] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   33.201355] Bluetooth: Core ver 2.15
[   33.201391] NET: Registered protocol family 31
[   33.201394] Bluetooth: HCI device and connection manager initialized
[   33.201398] Bluetooth: HCI socket layer initialized
[   33.202365] input: HP WMI hotkeys as /devices/virtual/input/input6
[   33.203399] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   33.215755] Linux video capture interface: v2.00
[   33.226505] usbcore: registered new interface driver btusb
[   33.235055] uvcvideo: Found UVC 1.00 device HP Webcam (090c:c371)
[   33.242239] input: HP Webcam as /devices/pci0000:00/0000:00:12.2/usb1/1-6/1-6:1.0/input/input7
[   33.242801] usbcore: registered new interface driver uvcvideo
[   33.242803] USB Video Class driver (v0.1.0)
[   33.284178] lib80211_crypt: registered algorithm 'TKIP'
[   33.284331] eth1: Broadcom BCM4328 802.11 Hybrid Wireless Controller 5.60.48.36 
[   33.339822] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   33.339917] HDA Intel 0000:00:14.2: setting latency timer to 64
[   33.375900] [fglrx] Maximum main memory to use for locked dma buffers: 2627 MBytes.
[   33.375958] [fglrx]   vendor: 1002 device: 9612 count: 1
[   33.376624] [fglrx] ioport: bar 1, base 0x7000, size: 0x100
[   33.376660] pci 0000:01:05.0: power state changed by ACPI to D0
[   33.376668] pci 0000:01:05.0: power state changed by ACPI to D0
[   33.376677] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   33.376683] pci 0000:01:05.0: setting latency timer to 64
[   33.378635] [fglrx] Kernel PAT support is enabled
[   33.378662] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[   33.461188] input: HDA ATI SB Mic at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   33.461424] input: HDA ATI SB Mic at Ext Drive Bar Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[   33.461632] input: HDA ATI SB HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[   33.462336] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   33.462383]   alloc irq_desc for 47 on node -1
[   33.462386]   alloc kstat_irqs on node -1
[   33.462397] HDA Intel 0000:01:05.1: irq 47 for MSI/MSI-X
[   33.462422] HDA Intel 0000:01:05.1: setting latency timer to 64
[   33.566083] r8169 0000:0a:00.0: eth0: link down
[   33.568770] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.577465] type=1400 audit(1286969791.866:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=938 comm="apparmor_parser"
[   33.580880] type=1400 audit(1286969791.870:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=938 comm="apparmor_parser"
[   33.581060] type=1400 audit(1286969791.870:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=938 comm="apparmor_parser"
[   33.584450] type=1400 audit(1286969791.874:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=937 comm="apparmor_parser"
[   33.586645] type=1400 audit(1286969791.874:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=951 comm="apparmor_parser"
[   33.595872] type=1400 audit(1286969791.882:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=951 comm="apparmor_parser"
[   33.605402] type=1400 audit(1286969791.894:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=967 comm="apparmor_parser"
[   34.422204] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1a0b1, caps: 0xa04751/0xa00000/0x0
[   34.556358] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   36.492045] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0001
[   36.686748] ppdev: user-space parallel port driver
[   36.897491] [fglrx] ATIF platform detected with notification ID: 0x81
[   37.246483] [fglrx] GART Table is not in FRAME_BUFFER range 
[   37.247381]   alloc irq_desc for 48 on node -1
[   37.247385]   alloc kstat_irqs on node -1
[   37.247396] fglrx_pci 0000:01:05.0: irq 48 for MSI/MSI-X
[   37.248137] [fglrx] Firegl kernel thread PID: 1264
[   37.248438] [fglrx] IRQ 48 Enabled
[   37.571182] [fglrx] Gart USWC size:864 M.
[   37.571186] [fglrx] Gart cacheable size:342 M.
[   37.571192] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   37.571196] [fglrx] Reserved FB block: Unshared offset:fffc000, size:4000 
[   41.707094] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   44.384515] eth1: no IPv6 routers present
[   75.332444] Bluetooth: L2CAP ver 2.14
[   75.332447] Bluetooth: L2CAP socket layer initialized
[   75.338855] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   75.338859] Bluetooth: BNEP filters: protocol multicast
[   75.344231] Bluetooth: SCO (Voice Link) ver 0.6
[   75.344234] Bluetooth: SCO socket layer initialized
[   75.449086] Bluetooth: RFCOMM TTY layer initialized
[   75.449093] Bluetooth: RFCOMM socket layer initialized
[   75.449095] Bluetooth: RFCOMM ver 1.11
[   76.206327] ip_tables: (C) 2000-2006 Netfilter Core Team
olga@olga-laptop:~$ 

It is not every 10 minutes, rather every n "actions" for lack of a better description. Please ask questions and help me in figuring out how to rid me of this problem. 

It took me 5 attempts and one hour just to write this message...

**[COLOR="DarkOrchid"]THANK YOU[/COLOR]**[/SIZE][/FONT]

---

