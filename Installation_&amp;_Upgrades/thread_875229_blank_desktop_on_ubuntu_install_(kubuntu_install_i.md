---
title: "blank desktop on ubuntu install (kubuntu install is fine)"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by c-roc on 2008-07-30
When I installed Ubuntu 8.04 on my roomie's computer, it results in a blank screen with mouse.
When I try Kubuntu it works fine.

I think I'd rather have Ubuntu because that's what I use and this guy doesn't even have an email address yet, so he's pretty green and I think Ubuntu's a little simpler.

So I'm guessing it's a gnome problem?  any ideas on what I can try?

thanx

---

### Post by spiderbatdad on 2008-07-30
did you verify the cd md5sum?  Can you post any specs regarding the computer?

---

### Post by c-roc on 2008-07-30
I'll run lshw when I get home and post the results.
the same disk was used in a couple other problem-free installs, but I haven't actually checked the md5sum.

---

### Post by c-roc on 2008-07-30
description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: GA-7VAXP
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: 1.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F11 (05/09/2003)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 1837MHz
          capacity: 2800MHz
          width: 32 bits
          clock: 167MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
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
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 768MiB
          capacity: 768MiB
        *-bank:0
             description: DIMM 266 MHz (3.8 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 256MiB
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM 333 MHz (3.0 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM 333 MHz (3.0 ns) [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: VT8377 [KT400/KT600 AGP] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8235 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
        *-storage
             description: RAID bus controller
             product: PDC20276 (MBFastTrak133 Lite)
             vendor: Promise Technology, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list
             configuration: driver=pata_pdc2027x latency=32 maxlatency=18 mingnt=4 module=pata_pdc2027x
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
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
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
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
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
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
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
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
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
             logical name: scsi2
             logical name: scsi3
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk
                description: ATA Disk
                product: Maxtor 6E040L0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@2:0.1.0
                logical name: /dev/sda
                version: NAR6
                serial: E13VDHJE
                size: 38GiB (41GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e94aeb46
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.1.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 6482e867-372f-4364-8798-d5d4912435a4
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2003-01-01 06:25:13 filesystem=ext3 modified=2008-07-29 21:15:22 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-07-27 19:34:47 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.1.0,2
                   logical name: /dev/sda2
                   size: 729MiB
                   capacity: 729MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 729MiB
                      capabilities: nofs
           *-cdrom
                description: CD-R/CD-RW writer
                product: CD-RW GCE-8400B
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@3:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=open
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
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 13
             bus info: pci@0000:00:13.0
             logical name: eth0
             version: 10
             serial: 00:20:ed:6d:f8:fc
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.200.177 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-firewire
             description: FireWire (IEEE 1394)
             product: IEEE 1394 Host Controller
             vendor: VIA Technologies, Inc.
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 46
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=32 module=ohci1394
     *-scsi
          physical id: 1
          bus info: usb@4:5
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: USB 2.0 Reader
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 1.05
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: USB 2.0 Reader
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
             version: 1.05
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: USB 2.0 Reader
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
             version: 1.05
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             product: USB 2.0 Reader
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
             version: 1.05
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde

---

### Post by spiderbatdad on 2008-07-30
Not sure what to suggest. I'm thinking it's a driver issue related to your video card. Google ubuntu GeForce FX 5200 might provide the answer.

Have you tried booting into safe graphics and then looking for a restricted driver in the Hardware Drivers menu?

This might work from a shell (recovery boot), of course you have to use apt-get, as you wont have a graphical environment:[http://ubuntuforums.org/archive/index.php/t-21554.html](http://ubuntuforums.org/archive/index.php/t-21554.html)

---

