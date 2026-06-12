---
title: "Problem with Install/Upgrade to 10.04 on Dell Inspiron 700m"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by hipowershooter on 2010-06-11
I have a Dell Inspiron 700m laptop. I have run versions 7 thru 9.10. My last upgrade was to 9.10. Recently, I installed a new 160 GB HDD on the laptop, installed 9.10 on it, and was able to move all my data/programs/settings to the new HDD. It worked flawlessly. Then I figured, why not upgrade to 10.04.

The upgrade looked like it went to completion, but on reboot there was nothing but a blank, backlit, faint screen. As I had my old drive to work with, I rebooted with that, searched for possible upgrade issues and finding none, figured what did I have to loose now. I downloaded the ISO for 10.04, burned it to a CD. Then I tore the laptop down, removed the old HDD, installed the new one, inserted the CD and let the new install proceed. It got as far as the "dots on the screen" flashing by, and then the screen went blank, as when I did the upgrade, and it just sat there.

Not to be outwitted, I went to my PC, copied the ISO from my old drive, and reburned a new CD, this time at a much slower speed, thinking I might have had a bad burn. Tried it again and same results. SO I downloaded the ISO again, and again burned a new CD at a slower speed, and tried again, same issue.

I am wondering if anyone else has experienced a similar or like issue with 10.04 and with a Dell Inspiron 700m? The only upgrades from the original laptop have been the new HDD which works fine with 9.1 and an memory upgrade using Crucial recommended memory (1GB added to original 256MB)

Hardware configurations below:
art-dell700m
    description: Portable Computer
    product: Inspiron 700m
    vendor: Dell Computer Corp.
    version: -1
    serial: 77XHS51
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.3
    configuration: boot=oem-specific chassis=portable uuid=44454C4C-3500-1053-8048-B1004F583737
  *-core
       description: Motherboard
       product: Inspiron 700m
       vendor: DELL SYSTEM
       physical id: 0
       version: Rev.A
       serial: CN0J508870166492C0YE
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 1
          version: A00 (06/21/04)
          size: 107KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.60GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.13.6
          slot: U1
          size: 1200MHz
          capacity: 1700MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back unified
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1280MiB
        *-bank:0
             description: SODIMM DDR Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: M1
             size: 256MiB
             width: 32 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: SODIMM DDR Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: M2
             size: 1GiB
             width: 32 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:11 memory:e8000000-efffffff(prefetchable) memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff(prefetchable) memory:e0080000-e00fffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:10 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:10 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:11 memory:e0100000-e01003ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:3000(size=4096) memory:e0200000-e02fffff memory:50000000-57ffffff(prefetchable)
           *-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:71:55:63
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.2 latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
                resources: irq:10 memory:e0206000-e0206fff
           *-pcmcia:0
                description: CardBus bridge
                product: PCI7420 CardBus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:10 memory:e0209000-e0209fff ioport:3000(size=256) ioport:3400(size=256) memory:50000000-53ffffff(prefetchable) memory:5c000000-5fffffff
           *-pcmcia:1
                description: CardBus bridge
                product: PCI7420 CardBus Controller
                vendor: Texas Instruments
                physical id: 4.1
                bus info: pci@0000:02:04.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:10 memory:e020a000-e020afff ioport:3800(size=256) ioport:3c00(size=256) memory:54000000-57ffffff(prefetchable) memory:60000000-63ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@0000:02:04.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: irq:10 memory:e0208000-e02087ff memory:e0200000-e0203fff
           *-storage
                description: Mass storage controller
                product: PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
                vendor: Texas Instruments
                physical id: 4.3
                bus info: pci@0000:02:04.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=32 maxlatency=4 mingnt=7
                resources: irq:10 memory:e0207000-e0207fff
           *-network:1
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 02
                serial: 00:0f:1f:af:2c:8a
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10MB/s
                resources: irq:10 memory:e0204000-e0205fff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:10 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:58000000-580003ff
           *-disk
                description: ATA Disk
                product: SAMSUNG HM160HC
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LQ10
                serial: S12TJDSZ427796
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00015a43
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 086085ef-f01a-4143-8122-cd1d5f5882a9
                   size: 145GiB
                   capacity: 145GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-06-10 13:09:29 filesystem=ext4 lastmountpoint=/ï¿œXï¿œ`ï¿œï¿œï¿œï¿œïï¿œï¿œï¿œ!ï¿œï¿œï¿œï¿œï¿œï¿œïï¿œï¿œeï¿œIï¿œï¿œIï¿œï¿œ`ï¿œï¿œï¿œï¿œïï¿œï¿œï¿œïï¿œï¿œEhï¿œ`ï¿œï¿œï¿œ&ï¿œE modified=2010-06-10 13:23:43 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-06-11 06:11:22 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3631MiB
                   capacity: 3631MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3631MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: CDRW/DVD CRX830E
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: KDK3
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1880(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:10 ioport:1c00(size=256) ioport:18c0(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
  *-battery
       product: ZCSMP-PA22
       vendor: ZCSMP-PA22
       physical id: 1
       slot: Left Side
       capacity: 44000mWh
       configuration: voltage=14.4V

---

### Post by bcbc on 2010-06-11
[http://c600g.blogspot.com/2010/05/installing-ubuntu-netbook-remix-1004-on.html](http://c600g.blogspot.com/2010/05/installing-ubuntu-netbook-remix-1004-on.html)
[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-10-04-lts-install-fail-black-screen-700m-813281/](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-10-04-lts-install-fail-black-screen-700m-813281/)

---

### Post by hipowershooter on 2010-06-13
Thanks for the feed back. I reloaded 9.10 as it was working and I am comfortable with it. I will look into "solutions" offered, but have to wonder why, with a major release, support for a previously working graphics card would be overlooked or forgotten? Many of us are turning to Linux to keep older hardware up and running. MS abandons older systems with each realease, but Linux had always supported them. Is there a change in the wind?

---

