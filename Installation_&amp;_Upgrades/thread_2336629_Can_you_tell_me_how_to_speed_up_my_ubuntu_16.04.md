---
title: "Can you tell me how to speed up my ubuntu 16.04"
date: 2016-09-09
forum: Installation &amp; Upgrades
---

### Post by seanbw2 on 2016-09-09
Problem: I installed Ubuntu 16.04 and as time went on, I found it slow. 
Then I ran out of disk space on my system drive because I deleted some files and they found their way into my home folder and occupied the majority of the space.
TheFU and Oldos2er were very helpful in resolving that problem.
Now I need more help to resolve the one issue that can frustrate me from going forward and it is the unbelievable slow speed the system is running at.
It is so bad that I am finding it unusable.
I dont know what the problem is. 
Initially I thought it was because the system was trawling through the hard disks but i have confirmed that it is not because I initially removed all the disks with the exception of the two system disks (long story short summary - I wanted to move my system partition from the 320GB disk to the TB disk. So I cloned the original system disk but that didn't work)
With only two disks, it was as slow. So I put the three other disks back to make up the pool I call "GenPool" 
No difference in speed.

The system specs are:
HP Gen 8 Proliant Server 16GB RAM Xeon CPU E31220. (It originally came with a Celeron chip but I changed it)
Can anyone guide me towards removing the speed blockage?
Please!


I am writing this on my Ubuntu 16.04 and it is painfully slow so I need to get the data that I need from here and then continue on my windows box.
My fstab is as follows:
```
 # /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdh1 during installation
UUID=3ef296db-9ce6-4d28-a878-1383ea1ac45d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdh4 during installation
UUID=fc0ae468-fef9-4129-8858-5addfd0183f5 none            swap    sw              0       0


### Mountpoints for Data Disks. ###
# OricO disks #
UUID=d63b97a8-7049-41b3-a80d-6079055f1d53 /mnt/data/OricO/1OricO001 auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0
UUID=b0e1c7dc-56ad-48ca-a980-e59231da4036 /mnt/data/OricO/1OricO002 auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0
UUID=0fdb085d-2371-4cc6-86f1-0f98e7e3721a /mnt/data/OricO/1OricO003 auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0
UUID=4285f2d0-e9a5-4bc1-9b91-18e08c30e376 /mnt/data/OricO/1OricO004 auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0


# GenPool disks #
# Where is GenG1610T001??? GenG1610T001 is the system disk
UUID=fc5f2e1a-32a0-4b72-971f-28828ef1cd42 /mnt/data/Gen/GenG1610T002 auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0
UUID=c41de965-ebea-4229-a2b0-e514be69bf67 /mnt/data/Gen/GenG1610T003 auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0
#UUID=d9695aba-a43c-431b-b6d5-28d137d852ed /mnt/data/Gen/GenG1610T005 auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0


# StartPool disks #
UUID=f495731a-407f-4bff-9b19-a5a7499c843e /mnt/data/StarT/1StarTech001 auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0
UUID=8bfc6a26-2a16-416a-92ca-ae9a579ddff6 /mnt/data/StarT/1StarTech002 auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0
UUID=c6dce86b-f3ee-4251-b33a-d76a8f95707d /mnt/data/StarT/1StarTech003 auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0
UUID=198d922d-1640-4a16-8175-005d79507f79 /mnt/data/StarT/1StarTech004 auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0
UUID=6f1b1b52-a404-4bb7-a249-382b25b75801 /mnt/data/StarT/1StarTech005 auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0
UUID=db5d0e3c-b56f-4e00-9f7d-a2965c3bc1b9 /mnt/data/StarT/1StarTech007 auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0
UUID=e7b15a40-4419-4b8b-9b9e-3130404bfc23 /mnt/data/StarT/1StarTech008 auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0


### Mountpoints for Parity Disks ###
UUID=b71b4b52-6ed8-48fc-9d89-f18ddea9299b /mnt/data/parity/1OricO005P auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0
UUID=4ffe7ed7-6381-421c-bc93-1bec6448ee37 /mnt/data/parity/GenG1610T004P auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0
UUID=8bdc1ab5-38df-4569-8b3c-347047893152 /mnt/data/parity/1StarTech006P auto nosuid,nodev,nofail,x-gvfs-show,defaults,errors=remount-ro 0 0


### MergerFS Pools.  I'd mount the pools some ###
/mnt/data/OricO/1OricO???  /media/OricoPool  fuse.mergerfs category.create=eplfs,defaults,allow_other,minfreespace=20G,fsname=OricoPool 0 00
/mnt/data/Gen/GenG1610T??? /media/GenPool  fuse.mergerfs category.create=eplfs,defaults,allow_other,minfreespace=20G,fsname=GenPool 0 00
/mnt/data/StarT/1StarTech??? /media/StartPool fuse.mergerfs category.create=eplfs,defaults,allow_other,minfreespace=20G,fsname=StartPool 0 00



```

my blkid list  is as follows (I have shut down the StartPool and OricoPool disks to see if they help with speed. No they have no impact.
```
device                   fs_type    label       mount point                  UUID-----------------------------------------------------------------------------------------------------------------
/dev/sda1                ext4       GenG1610T001 (not mounted)               3ef296db-9ce6-4d28-a878-1383ea1ac45d
/dev/sda2                                       (not mounted)                
/dev/sda3                vfat       EFI_BOOT    (not mounted)                08C1-D7A0
/dev/sda4                swap                   [SWAP]                       fc0ae468-fef9-4129-8858-5addfd0183f5
/dev/sdb1                ext4       GenG1610T003 /mnt/data/Gen/GenG1610T003  c41de965-ebea-4229-a2b0-e514be69bf67
/dev/sdc1                ext4       GenG1610T002 /mnt/data/Gen/GenG1610T002  fc5f2e1a-32a0-4b72-971f-28828ef1cd42
/dev/sdd1                ext4       GenG1610T004P /mnt/data/parity/GenG1610T004P 4ffe7ed7-6381-421c-bc93-1bec6448ee37
/dev/sde1                ext4       GenG1610T005 /                           583e7e13-685d-4c4d-bde7-4807a2d1b883
/dev/sde2                                       (not mounted)                
/dev/sde3                vfat       EFI_BOOT    (not mounted)                61D1-A851
/dev/sde4                swap                   [SWAP]                       5456ccc9-21c9-4d7c-aed0-916e3356d2e4
/dev/sdf1                vfat       GENG1610TSD /media/usb0                  0E0A-3628
/dev/sdg1                vfat       VID         /media/usb1                  55BA-8E92



```

The hardware specifications generated by lshw are as follows:
```
seanbw@nas:~$ sudo lshwnas                       
    description: Tower Computer
    product: ProLiant MicroServer Gen8 (819185-421)
    vendor: HP
    serial: CZ154802P2
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=tower family=ProLiant sku=819185-421 uuid=38313931-3835-435A-3135-343830325032
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: HP
          physical id: 0
          version: J06
          date: 07/16/2015
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Xeon(R) CPU E31220 @ 3.10GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: Intel(R) Xeon(R) CPU E31220 @ 3.10GHz
          slot: Proc 1
          size: 2808MHz
          capacity: 3100MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm epb tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 710
             slot: Processor 1 Internal L1 Cache
             size: 128KiB
             capacity: 192KiB
             capabilities: burst internal write-back data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 720
             slot: Processor 1 Internal L2 Cache
             size: 1MiB
             capacity: 1536KiB
             capabilities: burst internal write-back
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 730
             slot: Processor 1 Internal L3 Cache
             size: 8MiB
             capacity: 12MiB
             capabilities: burst internal write-back
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: NOT AVAILABLE
             vendor: UNKNOWN
             physical id: 0
             slot: PROC  1 DIMM  1
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: NOT AVAILABLE
             vendor: UNKNOWN
             physical id: 1
             slot: PROC  1 DIMM  2
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: Xeon E3-1200 Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=ie31200_edac
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:4000(size=4096) memory:fbf00000-fbffffff
           *-storage
                description: SATA controller
                product: ASM1062 Serial ATA Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:32 ioport:4000(size=8) ioport:4008(size=4) ioport:4010(size=8) ioport:4018(size=4) ioport:4020(size=32) memory:fbff0000-fbff01ff memory:fbf00000-fbf0ffff
        *-pci:1
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:21 memory:facf0000-facf03ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-36-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb:0
                      description: USB hub
                      product: USB2.0 Hub
                      vendor: VIA Labs, Inc.
                      physical id: 5
                      bus info: usb@1:1.5
                      version: 90.80
                      capabilities: usb-2.10
                      configuration: driver=hub slots=4 speed=480Mbit/s
                    *-usb:0
                         description: Generic USB device
                         product: 802.11 n WLAN
                         vendor: Ralink
                         physical id: 1
                         bus info: usb@1:1.5.1
                         version: 1.01
                         serial: 1.0
                         capabilities: usb-2.00
                         configuration: driver=rt2800usb maxpower=450mA speed=480Mbit/s
                    *-usb:1
                         description: Keyboard
                         product: Dell USB Keyboard
                         vendor: Dell
                         physical id: 2
                         bus info: usb@1:1.5.2
                         version: 3.50
                         capabilities: usb-1.10
                         configuration: driver=usbhid maxpower=70mA speed=2Mbit/s
                    *-usb:2
                         description: Bluetooth wireless interface
                         product: CSR8510 A10
                         vendor: Cambridge Silicon Radio, Ltd
                         physical id: 3
                         bus info: usb@1:1.5.3
                         version: 88.91
                         capabilities: bluetooth usb-2.00
                         configuration: driver=btusb maxpower=100mA speed=12Mbit/s
                    *-usb:3
                         description: Mouse
                         product: Dell Premium USB Optical Mouse
                         vendor: Dell Computer Corp.
                         physical id: 4
                         bus info: usb@1:1.5.4
                         version: 0.09
                         capabilities: usb-2.00
                         configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
                 *-usb:1
                      description: Human interface device
                      product: Back-UPS XS 700U   FW:924.Z3 .I USB FW:Z3
                      vendor: American Power Conversion
                      physical id: 6
                      bus info: usb@1:1.6
                      version: 1.06
                      serial: 3B1543X01276
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=24mA speed=2Mbit/s
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f8000000-f80fffff ioport:fab00000(size=1048576)
           *-network:0
                description: Ethernet interface
                product: NetXtreme BCM5720 Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eno1
                version: 00
                serial: b0:5a:da:87:d5:84
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5720-v1.37 NCSI v1.3.12.0 ip=192.168.0.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:16 memory:fabf0000-fabfffff memory:fabe0000-fabeffff memory:fabd0000-fabdffff memory:f8000000-f801ffff
           *-network:1
                description: Ethernet interface
                product: NetXtreme BCM5720 Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0.1
                bus info: pci@0000:03:00.1
                logical name: eno2
                version: 00
                serial: b0:5a:da:87:d5:85
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5720-v1.37 NCSI v1.3.12.0 ip=192.168.0.105 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:17 memory:fabc0000-fabcffff memory:fabb0000-fabbffff memory:faba0000-fabaffff memory:f8020000-f803ffff
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 memory:fbe00000-fbefffff
           *-usb
                description: USB controller
                product: uPD720201 USB 3.0 Host Controller
                vendor: Renesas Technology Corp.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:18 memory:fbef0000-fbef1fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.4.0-36-generic xhci-hcd
                   physical id: 0
                   bus info: usb@5
                   logical name: usb5
                   version: 4.04
                   capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.4.0-36-generic xhci-hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 4.04
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
        *-pci:5
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:3000(size=4096) memory:fad00000-fbdfffff ioport:f9000000(size=16777216)
           *-generic:0 UNCLAIMED
                description: System peripheral
                product: Integrated Lights-Out Standard Slave Instrumentation & System Support
                vendor: Hewlett-Packard Company
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: ioport:3000(size=256) memory:fbdf0000-fbdf01ff ioport:3400(size=256)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: MGA G200EH
                vendor: Matrox Electronics Systems Ltd.
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:f9000000-f9ffffff memory:fbde0000-fbde3fff memory:fb000000-fb7fffff
           *-generic:1
                description: System peripheral
                product: Integrated Lights-Out Standard Management Processor Support and Messaging
                vendor: Hewlett-Packard Company
                physical id: 0.2
                bus info: pci@0000:01:00.2
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=hpilo latency=0
                resources: irq:16 ioport:3800(size=256) memory:faff0000-faff00ff memory:fae00000-faefffff memory:fad80000-fadfffff memory:fad70000-fad77fff memory:fad60000-fad67fff memory:fad00000-fad0ffff
           *-usb
                description: USB controller
                product: Integrated Lights-Out Standard Virtual USB Controller
                vendor: Hewlett-Packard Company
                physical id: 0.4
                bus info: pci@0000:01:00.4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: msi pciexpress pm uhci bus_master cap_list
                configuration: driver=uhci_hcd latency=0
                resources: irq:16 ioport:3c00(size=32)
              *-usbhost
                   product: UHCI Host Controller
                   vendor: Linux 4.4.0-36-generic uhci_hcd
                   physical id: 1
                   bus info: usb@3
                   logical name: usb3
                   version: 4.04
                   capabilities: usb-1.10
                   configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:face0000-face03ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-36-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb
                      description: USB hub
                      product: Hub
                      vendor: Standard Microsystems Corp.
                      physical id: 3
                      bus info: usb@2:1.3
                      version: 8.01
                      capabilities: usb-2.00
                      configuration: driver=hub maxpower=2mA slots=2 speed=480Mbit/s
                    *-usb
                         description: Mass storage device
                         product: Ultra Fast Media Reader
                         vendor: Generic
                         physical id: 1
                         bus info: usb@2:1.3.1
                         logical name: scsi6
                         version: 2.09
                         serial: 000002660A01
                         capabilities: usb-2.00 scsi emulated scsi-host
                         configuration: driver=usb-storage maxpower=96mA speed=480Mbit/s
                       *-disk:0
                            description: SCSI Disk
                            physical id: 0.0.0
                            bus info: scsi@6:0.0.0
                            logical name: /dev/sdf
                            size: 60GiB (64GB)
                            capabilities: partitioned partitioned:dos
                            configuration: logicalsectorsize=512 sectorsize=512 signature=041c0717
                          *-volume
                               description: Windows FAT volume
                               vendor: SYSLINUX
                               physical id: 1
                               bus info: scsi@6:0.0.0,1
                               logical name: /dev/sdf1
                               logical name: /media/usb0
                               version: FAT32
                               serial: 0e0a-3628
                               size: 60GiB
                               capacity: 60GiB
                               capabilities: primary bootable fat initialized
                               configuration: FATs=2 filesystem=fat label=GENG1610TSD mount.fstype=vfat mount.options=rw,sync,nodev,noexec,noatime,nodiratime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
                       *-disk:1
                            description: SCSI Disk
                            physical id: 0.0.1
                            bus info: scsi@6:0.0.1
                            logical name: /dev/sdg
                            size: 256MiB (268MB)
                            capabilities: partitioned partitioned:dos
                            configuration: logicalsectorsize=512 sectorsize=512 signature=00000046
                          *-volume
                               description: Windows FAT volume
                               vendor: mkdosfs
                               physical id: 1
                               bus info: scsi@6:0.0.1,1
                               logical name: /dev/sdg1
                               logical name: /media/usb1
                               version: FAT32
                               serial: 55ba-8e92
                               size: 255MiB
                               capabilities: primary fat initialized
                               configuration: FATs=2 filesystem=fat label=VID mount.fstype=vfat mount.options=ro,sync,nodev,noexec,noatime,nodiratime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
        *-pci:6
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: C204 Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:10c0(size=8) ioport:10c8(size=4) ioport:10d0(size=8) ioport:10d8(size=4) ioport:10e0(size=16) ioport:10f0(size=16)
        *-ide:1
             description: IDE interface
             product: 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1400(size=8) ioport:1408(size=4) ioport:1410(size=8) ioport:1418(size=4) ioport:1420(size=16) ioport:1430(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: Hitachi HDS5C404
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: A3B0
             serial: PL1321LAGB3H5H
             size: 3726GiB (4TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=0309927d-30d3-40fc-9c63-233574b24085 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: 3ef296db-9ce6-4d28-a878-1383ea1ac45d
                size: 3351GiB
                capacity: 3351GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2016-06-09 22:38:42 filesystem=ext4 label=GenG1610T001 lastmountpoint=/media/xubuntu/GenG1610T001 modified=2016-09-07 20:34:02 mounted=2016-09-07 19:39:59 name=GenG1610T001 state=clean
           *-volume:1
                description: BIOS Boot partition
                vendor: EFI
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                serial: d632152c-0bbc-4d2e-a310-1f6f5b2882fa
                capacity: 37MiB
                capabilities: nofs
                configuration: name=bios_grub
           *-volume:2
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: FAT32
                serial: 08c1-d7a0
                size: 299MiB
                capacity: 300MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat label=EFI_BOOT name=efi_boot
           *-volume:3
                description: Linux swap volume
                vendor: Linux
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 1
                serial: fc0ae468-fef9-4129-8858-5addfd0183f5
                size: 374GiB
                capacity: 374GiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap name=linux-swap pagesize=4096
        *-disk:1
             description: ATA Disk
             product: ST4000DM000-1F21
             vendor: Seagate
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sdb
             version: CC52
             serial: Z3015TR7
             size: 3726GiB (4TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=2e61eb25-024c-42ad-9534-384ec0e6028d logicalsectorsize=512 sectorsize=4096
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sdb1
                logical name: /mnt/data/Gen/GenG1610T003
                version: 1.0
                serial: c41de965-ebea-4229-a2b0-e514be69bf67
                size: 3726GiB
                capacity: 3726GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2016-04-02 15:44:49 filesystem=ext4 label=GenG1610T003 lastmountpoint=/mnt/data/Gen/GenG1610T003 modified=2016-09-09 16:56:41 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,errors=remount-ro,data=ordered mounted=2016-09-09 16:56:41 name=GenG1610T003 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: Hitachi HDS5C404
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdc
             version: A3B0
             serial: PL2331LAGAP1AJ
             size: 3726GiB (4TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=b2ded8d0-a97d-4d9a-8c54-6fdc3f829bcf logicalsectorsize=512 sectorsize=4096
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdc1
                logical name: /mnt/data/Gen/GenG1610T002
                version: 1.0
                serial: fc5f2e1a-32a0-4b72-971f-28828ef1cd42
                size: 3726GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-06-03 18:24:03 filesystem=ext4 label=GenG1610T002 lastmountpoint=/mnt/data/Gen/GenG1610T002 modified=2016-09-09 16:56:41 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,errors=remount-ro,data=ordered mounted=2016-09-09 16:56:41 name=GenG1610T002 state=mounted
        *-disk:1
             description: ATA Disk
             product: ST4000DM000-1F21
             vendor: Seagate
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/sdd
             version: CC52
             serial: Z3015TFR
             size: 3726GiB (4TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=75b96725-5191-4981-b04c-93eb8d606ccb logicalsectorsize=512 sectorsize=4096
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.1.0,1
                logical name: /dev/sdd1
                logical name: /mnt/data/parity/GenG1610T004P
                version: 1.0
                serial: 4ffe7ed7-6381-421c-bc93-1bec6448ee37
                size: 3726GiB
                capacity: 3726GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2016-04-02 15:31:13 filesystem=ext4 label=GenG1610T004P lastmountpoint=/mnt/data/parity/GenG1610T004P modified=2016-09-09 16:56:41 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,errors=remount-ro,data=ordered mounted=2016-09-09 16:56:41 name=GenG1610T004P state=mounted
     *-scsi:2
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HCC54323
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sde
             version: A60W
             serial: E203421L16RUYP
             size: 298GiB (320GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=0309927d-30d3-40fc-9c63-233574b24085 logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sde1
                logical name: /
                version: 1.0
                serial: 583e7e13-685d-4c4d-bde7-4807a2d1b883
                size: 268GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-06-09 22:38:42 filesystem=ext4 label=GenG1610T005 lastmountpoint=/ modified=2016-09-09 16:56:28 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-09-09 16:56:38 name=GenG1610T005 state=mounted
           *-volume:1
                description: System partition
                vendor: EFI
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sde2
                serial: d632152c-0bbc-4d2e-a310-1f6f5b2882fa
                capacity: 3071KiB
                capabilities: boot
                configuration: name=bios_grub
           *-volume:2
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sde3
                version: FAT32
                serial: 61d1-a851
                size: 299MiB
                capacity: 300MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat label=EFI_BOOT name=efi_boot
           *-volume:3
                description: Linux swap volume
                vendor: Linux
                physical id: 4
                bus info: scsi@2:0.0.0,4
                logical name: /dev/sde4
                version: 1
                serial: 5456ccc9-21c9-4d7c-aed0-916e3356d2e4
                size: 29GiB
                capacity: 29GiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap name=linux-swap pagesize=4095
  *-power UNCLAIMED
       description: Power Supply 1
       vendor: HP
       physical id: 1
       capacity: 32768mWh
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1.5.1
       logical name: wlx0087407f0085
       serial: 00:87:40:7f:00:85
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.4.0-36-generic firmware=0.29 link=no multicast=yes wireless=IEEE 802.11bgn
seanbw@nas:~$ 



```

---

### Post by sudodus on 2016-09-09
I think you need a new graphics card to run Ubuntu at decent speed. Server computers are intended to run headless or with a simple 'console' monitor. I found some web pages, that confirmed that this is the problem.

Before you start looking for a new graphics card, I suggest that you try some flavours of Ubuntu with lighter desktop environments. It means that the graphics will be much more responsive, and you can play more demanding video clips.

- Lubuntu with the ultra light desktop environment LXDE
- Ubuntu MATE with the medium light desktop environment MATE
- Xubuntu with the medium light desktop environment XFCE

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by seanbw2 on 2016-09-10
I think you are right. I am going to install XFCE as I already have the desktop (only one Microsoft RDP will connect to) but does that mean I start from scratch and have to reinstall all my programs? 
That will be a bummer.

---

### Post by uRock on 2016-09-10
You can install XFCE without completing a reinstall just run,```
sudo apt-get install xfce-4
```

---

### Post by Bucky Ball on 2016-09-10
> **uRock said:**
> You can install XFCE without completing a reinstall just run,```
sudo apt-get install xfce-4
```

Yep. Then reboot and log in to the xfce4 session. You can install lxde the same way.

---

### Post by seanbw2 on 2016-09-15
Thanks. I will install and confirm.

---

### Post by ian-weisser on 2016-09-15
> **seanbw2 said:**
> but does that mean I start from scratch and have to reinstall all my programs? 
That will be a bummer.

That's why you keep notes. And versioned data backups.
ALWAYS assume your system will fail someday, and you must rebuild it from scratch on different hardware.
The pleasure of Linux comes from keeping those meltdowns very few and far between.

...or worse, you will need to talk an on-site person through the rebuilding process...by phone.

---

