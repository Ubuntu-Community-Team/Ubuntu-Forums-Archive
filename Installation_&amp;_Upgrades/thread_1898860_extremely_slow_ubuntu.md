---
title: "extremely slow ubuntu"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by droa on 2011-12-22
i have installed ubuntu 11.10 to my girlfriends computer instead of windows vista. at the beginning everything was normal by step by step all operating system went too slow.

even though i've changed the desktop environment with xcfe, unfortunately ubuntu is working extremely slow.

```
ludo lshw
```  

```
droa@droa:~$ sudo lshw
[sudo] password for droa:
droa                 
    description: Computer
    version: ble
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=0073D50A-F11F-0F10-AB28-8D8D01F52141
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: C3C31
          date: 12/24/2007
          size: 100KiB
          capacity: 960KiB
          capabilities: _sa pc_ pcmc_a pnp upgrade shadowing escd cdboot acp_ usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: U2E1
          size: 1867MHz
          capacity: 4096MHz
          width: 64 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 4MiB
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
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 533 MHz (1,9 ns)
             product: SODIMM000
             vendor: Mfg 0
             physical id: 0
             serial: 1234-B0
             slot: M1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 533 MHz (1,9 ns)
             product: SODIMM001
             vendor: Mfg 1
             physical id: 1
             serial: 1234-B1
             slot: M2
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
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
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:cc000000-ceffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G86 [GeForce 8400M GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:ce000000-ceffffff memory:d0000000-dfffffff memory:cc000000-cdffffff ioport:2000(size=128)
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhc_ bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhc_ bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1820(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehc_ bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:f0b04000-f0b043ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:47 memory:f0b00000-f0b03fff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:7000(size=4096) memory:f0700000-f07fffff ioport:84600000(size=2097152)
           *-network DISABLED
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 02
                serial: 00:19:d2:8a:90:9d
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=3.0.0-14-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
                resources: irq:46 memory:f0700000-f0700fff
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:f0600000-f06fffff ioport:84000000(size=1048576)
           *-network
                description: Ethernet interface
                product: 88E8055 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 13
                serial: 00:1b:24:e5:6a:be
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.14 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:45 memory:f0600000-f0603fff ioport:3000(size=256) memory:84000000-8401ffff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:6000(size=4096) memory:84200000-843fffff ioport:84400000(size=2097152)
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:4000(size=4096) memory:f0400000-f05fffff ioport:f0000000(size=4194304)
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhc_ bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1840(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhc_ bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1860(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhc_ bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1880(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehc_ bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0b04400-f0b047ff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:5000(size=4096) memory:f0800000-f08fffff ioport:80000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:0b:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:20 memory:f0804000-f0804fff ioport:5000(size=256) ioport:5400(size=256) memory:80000000-83ffffff memory:88000000-8bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 9.1
                bus info: pci@0000:0b:09.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohc_ bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=3
                resources: irq:21 memory:f0806000-f08067ff memory:f0800000-f0803fff
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 9.2
                bus info: pci@0000:0b:09.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
                resources: irq:20 memory:f0805000-f0805fff
           *-generic
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 9.3
                bus info: pci@0000:0b:09.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=57 maxlatency=4 mingnt=7
                resources: irq:20 memory:f0806800-f08068ff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:18e0(size=16) ioport:18d0(size=16)
           *-disk
                description: ATA Disk
                product: TOSHIBA MK1252GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LV01
                serial: 58QGF2YRS
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000c827a
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 9b514815-7b77-46d4-badc-f5f07ab29b2d
                   size: 109GiB
                   capacity: 109GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-12-17 22:04:15 filesystem=ext4 lastmountpoint=/ modified=2011-12-17 22:49:24 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-12-19 17:29:30 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2044MiB
                   capacity: 2044MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2044MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD RW AD-5530A
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AX32
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:84100000-841000ff ioport:1c00(size=32)
  *-battery
       description: Lithium Ion Battery
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1
       slot: Rear
       capacity: 1000mWh
       configuration: voltage=0,0V
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 2
       capabilities: inbound
droa@droa:~$ 
```

---

### Post by dino99 on 2011-12-22
Such config might run ubuntu smootly. How have you made the installation ? Have you checked graphic driver activation after the first reboot (with : sudo jockey-gtk) ?

But a possible reason is "my girlfriends", too many can drastically drop you down on knees :)

---

