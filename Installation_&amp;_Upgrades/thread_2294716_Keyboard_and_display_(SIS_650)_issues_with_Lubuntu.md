---
title: "Keyboard and display (SIS 650) issues with Lubuntu 14.04 install"
date: 2015-09-12
forum: Installation &amp; Upgrades
---

### Post by oli9 on 2015-09-12
Hi,

Total Linux noob here but thought I'd share some details of my recent Lubuntu install as it didn't go as smoothly as it should have! I've actually installed a couple of Linux variants on old machines previously but only for pals who had previously been running XP and had wanted something to give their machines a new lease of life. One of those installs was Lubuntu and that went without any issues.

Anyway, my old man gave me a old RM laptop, a CY-25 and I thought I'd create a dual boot netbook with it. lshw output follows:

```
computer
    description: Notebook
    product: CY25
    vendor: RM plc
    version: CY25
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific chassis=notebook uuid=[REMOVED]
  *-core
       description: Motherboard
       product: ACY25
       vendor: COMPAL
       physical id: 0
       version: N/A
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: CY25_1.16.T01
          date: 10/07/2003
          size: 100KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery
     *-cpu
          description: CPU
          product: Mobile Intel(R) Pentium(R) 4 - M CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: uPGA479M Socket
          size: 1800MHz
          capacity: 1800MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 768MiB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM0
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM1
             size: 256MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: 650/M650 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=64
          resources: irq:0 memory:e8000000-ebffffff
        *-pci
             description: PCI bridge
             product: AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:a000(size=4096) memory:ec100000-ec1fffff memory:f0000000-f7ffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 65x/M650/740 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller cap_list
                configuration: latency=0
                resources: memory:f0000000-f7ffffff memory:ec100000-ec11ffff ioport:a000(size=128)
        *-isa
             description: ISA bridge
             product: SiS961 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2/3 SMBus controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:8080(size=32)
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:10 memory:ec000000-ec000fff
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:10 memory:ec001000-ec001fff
        *-ide
             description: IDE interface
             product: 5513 IDE Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:9480(size=16)
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=173 maxlatency=11 mingnt=52
             resources: ioport:8400(size=256) ioport:9000(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: SiS7012 AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=173 maxlatency=11 mingnt=52
             resources: irq:5 ioport:8800(size=256) ioport:9080(size=128)
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
             vendor: VIA Technologies, Inc.
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 46
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=32
             resources: irq:5 memory:ec002000-ec0027ff ioport:9400(size=128)
        *-network:0
             description: Ethernet interface
             product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 6
             bus info: pci@0000:00:06.0
             logical name: eth0
             version: 10
             serial: [REMOVED]
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
             resources: irq:10 ioport:8c00(size=256) memory:ec002800-ec0028ff
        *-pcmcia:0
             description: CardBus bridge
             product: CB1420 Cardbus Controller
             vendor: ENE Technology Inc
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:10 memory:30000000-30000fff ioport:1000(size=256) ioport:1400(size=256) memory:34000000-37ffffff memory:38000000-3bffffff
        *-pcmcia:1
             description: CardBus bridge
             product: CB1420 Cardbus Controller
             vendor: ENE Technology Inc
             physical id: 9.1
             bus info: pci@0000:00:09.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:10 memory:3c000000-3c000fff ioport:1800(size=256) ioport:1c00(size=256) memory:40000000-43ffffff memory:44000000-47ffffff
        *-network:1
             description: Wireless interface
             product: ISL3874 [Prism 2.5]/ISL3872 [Prism 3]
             vendor: Intersil Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             logical name: wlan0
             version: 01
             serial: [REMOVED]
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list ethernet physical wireless logical
             configuration: broadcast=yes driver=hostap firmware=1.4.9 latency=64 multicast=yes wireless=IEEE 802.11b
             resources: irq:10 memory:ec400000-ec400fff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: FUJITSU MHS2040A
             vendor: Fujitsu
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 8004
             serial: [REMOVED]
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=7c217c21
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 17GiB
                capacity: 17GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-09-22 10:26:41 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 12GiB
                capacity: 12GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 976MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /
                   capacity: 11GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: CDRW/DVD SBW-241
             vendor: QSI
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: VY02
             serial: [REMOVED]
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
  *-battery
       physical id: 1
       slot: Right Front
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:2
       logical name: wlan1
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.19.0-28-generic firmware=0.29 ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11bgn


```

 I followed the install guides to the letter. First I shrank the existing XP partition and created new install and swap partitions (8GB and 1GB respectively). I couldn't get the ISO to boot from USB so had to create a DVD but, running the option to try without installing, everything looked fine at first glance including the screen resolution of 1240x768.

However when I installed, having set the region settings to en-GB the keyboard defaulted to en-US initially and the screen resolution set itself to 600x800. The keyboard issue was easily fixed by changing the Keyboard Layout Handler Settings but there were no options in the Monitor Settings other than 600x800 and Auto, which changed nothing. Googling the SIS 650/740 chipset I came across plenty of Linux threads, mainly describing how to create and add a new display mode in XRandR. I tried following various advice but I was unable to create a new display mode, I only got errors. To cut a long story short I created a xorg.conf file and rebooted, ready to edit it and add the resolution settings I desired, only to find that this in itself had rectified the issue. The resolution 1024x768 now appears in the Monitor Settings.

I'm puzzled as xorg.conf doesn't come with Lubuntu by default and I didn't configure it so why did just creating it fix the problem? I'm also puzzled by the fact that the resolution seemed fine when I was trialling Lubuntu from the ISO. To my mind that suggests the driver to run the chipset exists in the release build but somehow wasn't assigned properly. Anyone got any ideas?

---

