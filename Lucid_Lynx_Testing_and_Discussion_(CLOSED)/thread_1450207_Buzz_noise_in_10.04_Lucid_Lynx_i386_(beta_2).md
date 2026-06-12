---
title: "Buzz noise in 10.04 Lucid Lynx i386 (beta 2)"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Virus666 on 2010-04-08
Hi all,

I have a serious buzz noise with 10.04 Lucid Lynx i386 (beta 2) in my   notebook.

It's a HP Pavilion dv6000 (dv6185ea) and there was no such a problem   with 8.10 Intrepid Ibex, 9.04 Jaunty Jackalope, Windows XP and Windows   7. However from 9.10 Karmic Koala there is a annoying buzz noise coming   from the internal speakers. The interesting thing is that whenever I   plug an external speaker, the noise does not disappear, moreover muting   the system does not change the situation.

I thing it's a Pulseaudio issue; when I force the PC to do anything   (such as moving the mouse) the noise disappears, but after that the buzz   noise appears again... It's a slight noise, however after half an  hour,  you got an awful headache because of that noise...

Here is my system information:

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML   and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML   and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition   Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1   (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2   (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3   (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI   Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI   Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI   Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI   Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI   Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface   Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA   IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev   02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go   7400] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG   [Golan] Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet   Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro   Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev   0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host   Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev   ff)
``````
cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xde300000 irq 22[/QUOTE][QUOTE]cat   /proc/asound/version
Advanced Linux Sound Architecture Driver Version   1.0.21.
``````
aplay -l
**** PLAYBACK Donan&#305;m Ayg&#305;tlar&#305;n&#305;n Listesi ****
kart 0: Intel [HDA Intel], ayg&#305;t 0: CONEXANT Analog [CONEXANT Analog]
  Altayg&#305;tlar: 1/1
  Altayg&#305;t #0: subdevice #0
kart 0: Intel [HDA Intel], ayg&#305;t 1: Conexant Digital [Conexant Digital]
  Altayg&#305;tlar: 1/1
  Altayg&#305;t #0: subdevice #0
``````
sudo lshw
description: Notebook
    product: HP Pavilion dv6000 (RP948EA#AB8)
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF703202D
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2   uuid=434E4636-3433-3058-4B47-0016369DE3D9
  *-core
       description: Motherboard
       product: 30BC
       vendor: Quanta
       physical id: 0
       version: 66.42
       serial: None
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.2D (11/26/2008)
          size: 100KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot   bootselect int5printscreen int9keyboard int14serial int17printer acpi   usb agp smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: U2E1
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          clock: 667MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae   mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse   sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts   aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm   lahf_lm tpr_shadow cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back
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
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          capabilities: vmx ht cpufreq
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
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express   Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express   PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 memory:dc000000-ddffffff   ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G72M [GeForce Go 7400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:dd000000-ddffffff   memory:c0000000-cfffffff(prefetchable) memory:dc000000-dcffffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:de300000-de303fff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096)   memory:d8000000-d9ffffff ioport:d2000000(size=33554432)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 02
                serial: 00:19:d2:37:ab:b9
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list   ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0   multicast=yes wireless=IEEE 802.11abg
                resources: irq:29 memory:d8000000-d8000fff
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:3000(size=4096)   memory:d6000000-d7ffffff ioport:d0000000(size=33554432)
        *-pci:3
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:4000(size=4096)   memory:da000000-dbffffff ioport:d4000000(size=33554432)
           *-network
                description: Ethernet interface
                product: 82573L Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 00
                serial: 00:16:36:9d:e3:d9
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list   ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd   autonegotiation
                configuration: autonegotiation=on broadcast=yes   driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.5-1   ip=192.168.2.2 latency=0 link=yes multicast=yes port=twisted pair   speed=100MB/s
                resources: irq:28 memory:da000000-da01ffff   ioport:4000(size=32)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1800(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1820(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1840(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1860(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:de304000-de3043ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:de000000-de0fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 5
                bus info: pci@0000:07:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4   mingnt=2
                resources: irq:16 memory:de000000-de0007ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 5.1
                bus info: pci@0000:07:05.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:17 memory:de000800-de0008ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 5.2
                bus info: pci@0000:07:05.2
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=ricoh-mmc latency=0
                resources: irq:11 memory:de000c00-de000cff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 5.3
                bus info: pci@0000:07:05.3
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
                resources: memory:de001000-de0010ff
           *-generic:3 UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 5.4
                bus info: pci@0000:07:05.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
                resources: memory:de001400-de0014ff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6   ioport:170(size=8) ioport:376 ioport:18b0(size=16)
           *-disk
                description: ATA Disk
                product: ST9120821AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 7.24
                serial: 5PL3WP1L
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=4a4e4a4e
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: f4451c3a-0249-49c6-90ad-195fd778d3e3
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary journaled extended_attributes   large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-04-07 16:58:18   filesystem=ext4 lastmountpoint=/7&#65533;&#1344;&#1312;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;[   &#65533;&#65533;M/&#65533;&#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;s&#65533;&#65533;&#65533;s&#65533;&#65533;&#65533;&#1312;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;]^ modified=2010-04-08 18:38:01   mount.fstype=ext4   mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered   mounted=2010-04-08 22:18:35 state=mounted
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1.0
                   serial: af18f528-40ef-4b7a-b7f1-d174ad2f10cb
                   size: 30GiB
                   capacity: 30GiB
                   capabilities: primary journaled extended_attributes   large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-02-12 01:14:15   filesystem=ext4 lastmountpoint=/mnt/migrationassistant&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;H&#1582;&#511;&#65533;&#65533;&#65533;^&#65533;&#65533;&#65533;6   &#65533;]'/&#65533;&#65533;^&#65533;&#65533;n&#65533; &#65533;&#65533;E modified=2010-04-08 21:37:25 mounted=2010-04-08  21:30:16  state=clean
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: 5a7941ee-7a4c-4eb0-a9dc-45d355cf9736
                   size: 1953MiB
                   capacity: 1953MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:3
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: 1.0
                   serial: 306f2480-8cbc-4569-9431-8bb1ac08bf8f
                   size: 59GiB
                   capacity: 59GiB
                   capabilities: primary journaled extended_attributes   large_files ext3 ext2 initialized
                   configuration: created=2009-11-24 16:22:38   filesystem=ext3 label=Depo modified=2010-04-08 21:37:25   mounted=2010-04-08 21:30:17 state=clean
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-851S
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.50
                capabilities: removable audio cd-r cd-rw dvd dvd-r   dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18c0(size=32)
```I'm desperately need   some assistance to fix that problem, since that problem I'm still using   Ubuntu 9.04 Jaunty Jackalope and it seems that its support has became   infrequent... If any code and information that I need to give is   existed, please tell me...

Thank you... :)

---

### Post by lidex on 2010-04-08
Seems you're just having all sorts of sound problems. Have a look here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio")

If you want to update alsa, use the link in my sig rather than that page, however. Also alsa-backports are available for lucid.

---

