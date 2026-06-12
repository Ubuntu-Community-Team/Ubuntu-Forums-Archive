---
title: "Cannot login to Ubuntu or Ubuntu Classic on new install (Dell Inspiron M5030)"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by bijit on 2011-09-12
I have installed Ubuntu 11.04 on Dell Inspiron M5030 (AMD Phenom II P360 CPU and Radeon HD 4250 graphics). However I cannoy log in to either Ubuntu (i.e. Unity) or Ubuntu Classic session. All I get after logging in is a screen with only the wallpaper, and no desktop. There is no panels or icons. 
However Ubuntu Classic (no effects) works. I have tried with both the open source drivers and FGLRX. When I try to start compiz from the Ubuntu Classic (using compiz --replace) I get the same blank desktop with the wallpaper.

Here is the output:
```
lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]

```
```
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD RS880
OpenGL version string:  2.1 Mesa 7.12-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

```

```
sudo lshw
[sudo] password for bijit: 
bijit-laptop              
    description: Portable Computer
    product: Inspiron M5030 (To be filled by O.E.M.)
    vendor: Winbond Electronics
    version: A05
    serial: JCRQHP1
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=portable cpus=2 sku=To be filled by O.E.M. uuid=44454C4C-4300-1052-8051-CAC04F485031
  *-core
       description: Motherboard
       product: 0C8PJJ
       vendor: Winbond Electronics
       physical id: 0
       version: A05
       serial: .JCRQHP1.CN7016616K04R3.
       slot: To Be Filled By O.E.M.
     *-cache:0
          description: L1 cache
          physical id: 5
          slot: L1-Cache
          size: 256KiB
          capacity: 256KiB
          capabilities: internal write-back unified
     *-cache:1
          description: L2 cache
          physical id: 6
          slot: L2-Cache
          size: 1MiB
          capacity: 1MiB
          capabilities: internal varies data
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: 8JSF25664HZ-1G4D1
             vendor: Micron Technology
             physical id: 0
             serial: 3A63759A
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: 8JSF25664HZ-1G4D1
             vendor: Micron Technology
             physical id: 1
             serial: 3A6375B9
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: SODIMM [empty]
             physical id: 2
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A05
          date: 03/03/2011
          size: 64KiB
          capacity: 1984KiB
          capabilities: mca pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) II P360 Dual-Core Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.6.3
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 800MHz
          capacity: 2300MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.6.3
          size: 800MHz
          capacity: 800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: Dell
             vendor: Winbond Electronics
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:fe700000-fe8fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: M880G [Mobility Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:11 memory:d0000000-dfffffff ioport:e000(size=256) memory:fe800000-fe80ffff memory:fe700000-fe7fffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:fea00000-feafffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 01
                serial: 90:a4:de:7a:d3:29
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.38-11-generic-pae firmware=N/A ip=192.168.1.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:fea00000-fea0ffff
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:fe900000-fe9fffff
           *-network
                description: Ethernet interface
                product: AR8152 v2.0 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: c1
                serial: 18:03:73:61:6a:d3
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:42 memory:fe900000-fe93ffff ioport:d000(size=128)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=16) memory:feb0a000-feb0a3ff
           *-disk
                description: ATA Disk
                product: WDC WD3200BEVT-7
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WX91AC0Y4444
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=411798c3
              *-volume:0
                   description: Windows FAT volume
                   vendor: Winbond Electronics
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT16
                   serial: 3030-3030
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=DellUtility
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 22c67097-a86e-6e40-a62d-689346aae900
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-02-26 19:49:15 filesystem=ntfs label=Recovery state=clean
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: cc829fba-12b6-49b8-8996-873daf998f9a
                   size: 22GiB
                   capacity: 22GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-09-11 18:32:47 filesystem=ext4 lastmountpoint=/ modified=2011-09-11 18:55:08 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-09-12 06:40:11 state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 260GiB
                   capacity: 260GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 6103MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 255GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW TS-L633C
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DW50
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb09000-feb09fff
        *-usb:1
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb08000-feb080ff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb07000-feb07fff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb06000-feb060ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:feb00000-feb03fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
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
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
        *-usb:4
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb05000-feb05fff
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb04000-feb040ff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 2
          bus info: usb@1:3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             size: 279GiB (300GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=c9a5f632
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/data disk
                version: 3.1
                serial: 0e4388d4-c522-bc42-ad7d-c932c752a62b
                size: 279GiB
                capacity: 279GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2004-09-07 14:05:51 filesystem=ntfs label=data disk mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
     *-scsi:1
          physical id: 3
          bus info: usb@3:1
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdc
  *-battery
       description: Lithium Ion Battery
       product: DELL 8NH5515
       vendor: SMP-SDI2.2
       physical id: 1
       serial: 14885
       slot: Sys. Battery Bay
       capacity: 44000mWh
       configuration: voltage=11.1V

```

---

### Post by ddarsow on 2011-09-19
I have been having exactly the same problem on my Dell M5010 with the same ATI Mobility 4200 video. Although I am starting to get used to the Classic Gnome w/ no effects option, it is aggravating. I am working on trying to fix it now and will let you know if I succeed.

---

