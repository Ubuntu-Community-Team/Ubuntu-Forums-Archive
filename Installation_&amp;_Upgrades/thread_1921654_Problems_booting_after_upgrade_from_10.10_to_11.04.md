---
title: "Problems booting after upgrade from 10.10 to 11.04"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by mameshiba on 2012-02-07
Hello,

Yesterday I tried to upgrade from 10.10 to 11.04 on my laptop via Update Manager. Everything seemed to go okay, but then when I restarted to complete the upgrade I couldn't log on because it hung on the screen with the Ubuntu logo and five red dots and did not load the login screen.

Earlier I went on someone else's machine to see if I could find anything useful in the forums and I found this post: [http://ubuntuforums.org/showthread.php?t=1921344](http://ubuntuforums.org/showthread.php?t=1921344) Using the advice by user jayshomebrew in there, I was able to load the GRUB menu and, by selecting 'Previous Linux Versions' and then '2.6.38-13 generic', log in as normal.

I followed the advice in the thread quoted above - removed the newer kernel and ran sudo update-grub in terminal - then rebooted. Only I still had the same problem as before. I've repeated this a couple of times but nothing changes; to log in I need to load the GRUB menu as previously described.

Once I'm logged in, System Monitor informs me I'm running 11.04 (Natty) and everything seems to work okay.

This is a list of my hardware:

> carrie@carrie-laptop:~$ sudo lshw
[sudo] password for carrie: 
carrie-laptop             
    description: Computer
    version: Rev. A1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=0090F598-025F-0000-0000-000000000000
  *-core
       description: Motherboard
       product: M7X0SUN
       vendor: clevo
       physical id: 0
       version: Bottom
       serial: SI96A-55
       slot: Bottom
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 6.00
          date: 09/16/2009
          size: 107KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: uPGA 479M
          size: 1200MHz
          capacity: 3600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cache
          description: L3 cache
          physical id: 7
          slot: L3 Cache
          size: 2MiB
          capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 4GiBu
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM2
             size: 2GiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 671MX
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:9000(size=4096) memory:d0000000-d2ffffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G98M [GeForce G 105M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:9000(size=128)
        *-isa
             description: ISA bridge
             product: SiS968 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1080(size=16)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:20 memory:d3304000-d3304fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:21 memory:d3305000-d3305fff
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:22 memory:d3306000-d3306fff
        *-network
             description: Ethernet interface
             product: 191 Gigabit Ethernet Adapter
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 02
             serial: 00:90:f5:98:02:5f
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.4 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
             resources: irq:19 memory:d3307000-d330707f ioport:1000(size=128)
        *-storage
             description: SATA controller
             product: AHCI IDE Controller (0106)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: scsi2
             logical name: scsi3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:17 ioport:10c8(size=8) ioport:10bc(size=4) ioport:10c0(size=8) ioport:10b8(size=4) ioport:10a0(size=16) memory:d3307400-d33075ff
           *-disk
                description: ATA Disk
                product: ST9500420AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 0002
                serial: 5VJ3JNE1
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000dda58
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 8d115567-6b38-4d41-bb0e-9e56d2160ec3
                   size: 457GiB
                   capacity: 457GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-05-27 03:45:07 filesystem=ext4 lastmountpoint=/ modified=2012-01-31 09:57:51 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2012-02-07 19:37:58 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 8852MiB
                   capacity: 8852MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 8852MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7700S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-pci:1
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=8192) memory:dc000000-dfffffff ioport:d3100000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:d3000000-d30fffff ioport:d3400000(size=2097152)
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:d3000000-d30000ff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:03:00.2
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:d3000400-d30004ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:03:00.3
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:16 memory:d3000800-d30008ff
        *-multimedia
             description: Audio device
             product: Azalia Audio Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=11 mingnt=52
             resources: irq:18 memory:d3300000-d3303fff
  *-remoteaccess UNCLAIMED
       vendor: SiS
       physical id: 1
       capabilities: inbound
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:2
       logical name: wlan0
       serial: 00:25:d3:96:a5:80
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=2.6.38-13-generic firmware=N/A ip=192.168.2.101 link=yes multicast=yes wireless=IEEE 802.11bg
carrie@carrie-laptop:~$

Apologies for the length, didn't want to risk missing anything out that might be important.

Anyone have any idea how I can fix this so it just loads the login screen without me having to access the GRUB menu?

Thanks in advance.

---

