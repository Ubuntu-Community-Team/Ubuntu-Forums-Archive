---
title: "Installation Software doesnt detect my disk"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by realninja on 2011-11-09
I want to install Ubuntu but it doesnt work. Gparted and Windows XP CD detect the hard disk even Ubuntu can see it but the installation software doesnt want to install anything anywhere. Does anyone have a clue?

See Picture [http://imageshack.us/photo/my-images/52/whynot.png/](http://imageshack.us/photo/my-images/52/whynot.png/)

lshw out
===============

ubuntu
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: KT400-8235
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 06/24/2003
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2600+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 2083MHz
          capacity: 3GHz
          width: 32 bits
          clock: 166MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1GiB
          capacity: 3GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 512MiB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 512MiB
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
     *-pci
          description: Host bridge
          product: VT8377 [KT400/KT600 AGP] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 80
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:c0000000-cfffffff
        *-pci
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: memory:e0000000-e1ffffff memory:d0000000-dfffffff
           *-display
                description: VGA compatible controller
                product: NV25 [GeForce4 Ti 4600]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
                resources: irq:16 memory:e0000000-e0ffffff memory:d0000000-d7ffffff memory:d8000000-d807ffff memory:d8080000-d809ffff
        *-network:0
             description: Wireless interface
             product: RT2561/RT61 rev B 802.11g
             vendor: Ralink corp.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: wlan0
             version: 00
             serial: 00:22:b0:75:12:a8
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rt61pci driverversion=3.0.0-12-generic firmware=0.8 ip=192.168.178.66 latency=32 link=yes multicast=yes wireless=IEEE 802.11bg
             resources: irq:18 memory:e3000000-e3007fff
        *-network:1
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: c
             bus info: pci@0000:00:0c.0
             logical name: eth0
             version: 10
             serial: 00:50:70:34:02:98
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
             resources: irq:19 ioport:d000(size=256) memory:e3008000-e30080ff memory:40000000-4000ffff
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d400(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d800(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:dc00(size=32)
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:e3009000-e30090ff
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e000(size=16)
           *-disk
                description: ATA Disk
                product: MAXTOR 6L080J4
                vendor: Maxtor
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: A93.
                serial: 664212359762
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0000937c
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 0c1a-6a80
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-11-09 16:17:38 filesystem=ntfs state=clean
           *-cdrom
                description: DVD-RAM writer
                product: SPD2413P
                vendor: PHILIPS
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: GP01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   capabilities: partitioned partitioned:dos
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=5db90e7d state=mounted
                 *-volume UNCLAIMED
                      description: Hidden HPFS/NTFS partition
                      physical id: 1
                      capacity: 695MiB
                      capabilities: primary bootable hidden
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:22 ioport:e400(size=256)

---

### Post by darkod on 2011-11-09
This usually happens if you were using the disk in raid and the raid data is not removed from it. If you are not running raid, boot into live mode with the cd and in terminal do:

sudo dmraid -E -r /dev/sda

Confirm that you want the raid data removed and that's it.

Note that if you ARE running raid this will DESTROY your array, so don't do it!!!

---

### Post by realninja on 2011-11-09
darkrod you are genius!!!! Thanks a lot!

---

### Post by darkod on 2011-11-09
You are welcome. Please mark the thread as Solved. You can do it from Thread Tools just above the first post.

---

