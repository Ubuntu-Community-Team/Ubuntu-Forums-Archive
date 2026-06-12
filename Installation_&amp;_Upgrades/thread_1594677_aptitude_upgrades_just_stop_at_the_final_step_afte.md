---
title: "aptitude upgrades just stop at the final step after upgrade to Maverick has completed"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by lifeboy on 2010-10-12
I have upgraded a recently installed 10.04 Ubuntu notebook (a Fujitsu Siemens Amilo Pro) to 10.10 using the updater.  All went smoothly, I rebooted and then attempted to reconfigure my graphics.

I use an external 19" Benq LCD monitor and in an attempt to configure Compiz I tried installing simple-ccsm along the lines of [http://www.unixmen.com/linux-tutorials/638-custom-compiz-effects-configuration-in-ubuntu-910-karmic-koala](http://www.unixmen.com/linux-tutorials/638-custom-compiz-effects-configuration-in-ubuntu-910-karmic-koala) which doesn't seem specific to 9.10 only, but also for later versions.

However, when I got to "libemeraldengine0", the process (apt-get install), just stopped and nothing happened on the "Unpacking replacement libemeraldengine0" line.  Nothing in the logs either.  So after 30 minutes or more I killed the terminal (ctl-c does nothing), deleted the lock files and repaired dpkg.  However, nothing seems to be able to install now.

I tried updating to a newer kernel by enabling the "proposed updates" in an effort to get a possible fix, but it also gets to the following state:

[HTML][FONT="Fixedsys"][SIZE="2"]
(Reading database ... 144862 files and directories currently installed.)
Preparing to replace linux-image-2.6.35-22-generic 2.6.35-22.33 (using .../linux-image-2.6.35-22-generic_2.6.35-22.34_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.35-22-generic ...
[/SIZE][/FONT][/HTML]

nothing more, no errors logged, just no response.

What could the problem be and how could I fix this?

My system info:

[HTML][FONT="Fixedsys"][SIZE="2"]
    description: Notebook
    product: AMILO Pro V2040
    vendor: FUJITSU SIEMENS
    version: 20
    serial: 9146IZ100354818CA0K00B
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=normal chassis=notebook uuid=558A6CC0-603E-11DA-9310-000AE4B0B88D
  *-core
       description: Motherboard
       product: AMILO Pro V2040
       vendor: FUJITSU SIEMENS
       physical id: 0
       serial: 9146IZ100354818CA0K00B
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R01-A1I (02/18/2006)
          size: 106KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: U1
          size: 1867MHz
          capacity: 2400MHz
          width: 32 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 2MiB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 1536MiB
          capacity: 3GiB
        *-bank:0
             description: DIMM DDR Synchronous
             physical id: 0
             slot: M1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous
             physical id: 1
             slot: M2
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
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
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:b0080000-b00fffff ioport:1800(size=8) memory:c0000000-cfffffff memory:b0040000-b007ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:66000000-6607ffff
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:41 memory:b0000000-b0003fff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:b4000000-b7ffffff ioport:d0000000(size=67108864)
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:b0004000-b00043ff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:3000(size=4096) memory:b8000000-b80fffff ioport:60000000(size=100663296)
           *-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 5
                bus info: pci@0000:06:05.0
                logical name: eth1
                version: 05
                serial: 00:13:ce:98:1d:9f
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=172.16.3.58 latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:20 memory:b8006000-b8006fff
           *-network:1
                description: Ethernet interface
                product: RTL-8169 Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:06:07.0
                logical name: eth0
                version: 10
                serial: 00:0a:e4:b0:b8:8d
                size: 10MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
                resources: irq:20 ioport:3000(size=256) memory:b8007000-b80070ff memory:64000000-6401ffff
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:06:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:22 memory:b8008000-b8008fff ioport:3400(size=256) ioport:3800(size=256) memory:60000000-63ffffff memory:68000000-6bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 9.2
                bus info: pci@0000:06:09.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:22 memory:b8007800-b8007fff memory:b8000000-b8003fff
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 9.3
                bus info: pci@0000:06:09.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
                resources: irq:22 memory:b8004000-b8005fff
           *-generic
                description: SD Host controller
                product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
                vendor: Texas Instruments
                physical id: 9.4
                bus info: pci@0000:06:09.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=57 maxlatency=4 mingnt=7
                resources: irq:22 memory:b8009400-b80094ff memory:b8009000-b80090ff memory:b8007400-b80074ff
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
           *-cdrom
                description: DVD writer
                product: DVD+-RW ND-6650A
                vendor: _NEC
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.42
                serial: [_NEC    DVD+-RW ND-6650A1.4205040800
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:18c8(size=8) ioport:18c0(size=4) ioport:18a8(size=8) ioport:180c(size=4) ioport:18b0(size=16) memory:b0004400-b00047ff
           *-disk
                description: ATA Disk
                product: SAMSUNG HM080JI
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: YC10
                serial: S082J10A110412
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0001cd7e
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 0d3678cc-e2ba-4b3d-af26-aa4689e19702
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-10-07 19:02:16 filesystem=ext4 lastmountpoint=/&#65533;w&#65533;&#65533;&#65533;hJK&#65533;&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;l!&#65533;hJK&#65533;@&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;&#65533;&#65533;h&#65533;&#65533;&#65533;yo!&#65533;&#65533;d modified=2010-10-07 18:49:15 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-10-12 17:11:39 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 1427MiB
                   capacity: 1427MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1427MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18e0(size=32)
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
[/FONT][/SIZE][/HTML]

---

### Post by lifeboy on 2010-10-12
> 
However, when I got to "libemeraldengine0", the process (apt-get install), just stopped and nothing happened on the "Unpacking replacement libemeraldengine0" line.  Nothing in the logs either.  So after 30 minutes or more I killed the terminal (ctl-c does nothing), deleted the lock files and repaired dpkg.  However, nothing seems to be able to install now.


I went back to in history to see what I had attempted to install with emerald and then used 

apt-get purge <all the packages tried to install including emerald>

This firstly attempted to install the new kernel I had starting installing before and then removed all the packages requested in the above command.

And now all seems to be back to normal!

---

