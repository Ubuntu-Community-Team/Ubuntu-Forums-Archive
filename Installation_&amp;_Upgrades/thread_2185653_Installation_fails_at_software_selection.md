---
title: "Installation fails at software selection"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by Matteo Iervasi on 2013-11-03
I've got an old Acer TravelMate 2434WLMi, and a week ago I uninstalled Windows XP because it was too slow...

So I tried to install Lubuntu, but if I try to use desktop iso I can't make it running: it sticks when it loads X session in an infinite loop.

SO I downloaded the alternate iso, but the installation fails when it has to select and install software (the main part :mad:)...

I tried different versions of Lubuntu, but everyone fails. I managed to install Ubuntu 10.04, but canonical does no longer support it, and I'm using Debian 7, but I don't feel confortable with it, I prefer *buntu..

Anyone can help me?

(Sorry for my poor english...)

---

### Post by mörgæs on 2013-11-03
Please run (using any Buntu version)

```
sudo lshw -sanitize > lshw.txt
```

and post lshw.txt in CODE tags. I'm afraid we have a SIS problem.

---

### Post by Matteo Iervasi on 2013-11-04
Thank for replying.
Here is the output:
```

computer
    description: Computer
    product: TravelMate 2430
    vendor: Acer, inc.
    version: Not Applicable
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=203E1D10-7688-D811-8D58-00163651EB2A
  *-core
       description: Motherboard
       product: Lugano
       vendor: Acer, Inc.
       physical id: 0
       version: Not Applicable
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: 3A22 (03/20/06)
          size: 100KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video usb
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: Socket 479M
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts
        *-cache
             description: L2 cache
             physical id: 8
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 512MiB
          capacity: 3GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM [empty]
             physical id: 1
             slot: DIMM2
        *-bank:2
             description: DIMM DRAM [empty]
             physical id: 2
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=64
          resources: irq:0 memory:e0000000-e1ffffff
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:9000(size=4096) memory:e2100000-e21fffff memory:e8000000-efffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=0
                resources: memory:e8000000-efffffff(prefetchable) memory:e2100000-e211ffff ioport:9000(size=128)
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:8100(size=32)
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1000(size=16)
           *-disk
                description: ATA Disk
                product: TOSHIBA MK3021GA
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: GA12
                serial: [REMOVED]
                size: 27GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00086506
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: [REMOVED]
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2013-11-03 15:01:10 filesystem=ext4 lastmountpoint=/arget modified=2013-11-03 18:41:50 mounted=2013-11-03 18:41:50 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 890MiB
                   capacity: 890MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 890MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVDRW SSW-8015S
                vendor: Slimtype
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: HRS2
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=173 maxlatency=11 mingnt=52
             resources: ioport:1400(size=256) ioport:1080(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=173 maxlatency=11 mingnt=52
             resources: irq:18 ioport:1c00(size=256) ioport:1800(size=128)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:e2000000-e2000fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:e2001000-e2001fff
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: irq:23 memory:e2002000-e2002fff
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: [REMOVED]
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
             resources: irq:19 ioport:2000(size=256) memory:e2003000-e2003fff memory:28000000-2801ffff(prefetchable)
        *-pcmcia
             description: CardBus bridge
             product: CB1410 Cardbus Controller
             vendor: ENE Technology Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:19 memory:28020000-28020fff ioport:2400(size=256) ioport:2800(size=256) memory:20000000-23ffffff(prefetchable) memory:24000000-27ffffff
        *-network:1
             description: Network controller
             product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=b43-pci-bridge latency=64
             resources: irq:17 memory:e2004000-e2005fff
  *-remoteaccess UNCLAIMED
       vendor: SiS
       physical id: 1
       capabilities: inbound
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

---

### Post by mörgæs on 2013-11-04
Yes, you have SIS graphics. I recommend Bodhi as mentioned in my signature. There are ways to get 13.10 working on a SIS platform but for a beginner I believe Bodhi is the easiest.

If you get some additional RAM you will have a much faster system.

---

