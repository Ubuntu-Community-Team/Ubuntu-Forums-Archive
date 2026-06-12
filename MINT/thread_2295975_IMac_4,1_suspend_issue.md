---
title: "IMac 4,1 suspend issue"
date: 2015-09-22
forum: MINT
---

### Post by nef1312 on 2015-09-22
I recently installed Mint 17.2 Xfce on an old Imac 4,1 (vintage January 2006) and am dual booting it along with OSX. It has an Intel dual core (not to be confused with the core 2 dual) processor. Nearly everything works very well in Mint - in fact, it runs like a brand new computer and, at this point, much better than with OSX. The exception is suspend to RAM and, on occasion, switching off the screen. I would like suspend to RAM to work, even though the IMac is an all-in-one, not a laptop, and, clearly, it would be much, much better of the screen would always switch off at the time it is supposed to do so. The specs, using LSHW, for the Imac are as follows:

```
     description: All In One
    product: iMac4,1 (System SKUNumber)
    vendor: Apple Computer, Inc.
    version: 1.0
    serial: W86084DTU2P
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=all-in-one family=Napa Mac sku=System SKUNumber uuid=9CFE245E-D0C8-BD45-A79F-54EA5FBD3D97
  *-core
       description: Motherboard
       product: Mac-F42787C8
       vendor: Apple Computer, Inc.
       physical id: 0
       version: PVT
       serial: 1
       slot: Part Component
     *-firmware
          description: BIOS
          vendor: Apple Computer, Inc.
          physical id: 0
          version: IM41.88Z.0055.B08.0610121350
          date: 10/12/06
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect acpi ieee1394boot smartbattery netboot
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU            1500  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 11c
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U2E1
          size: 2GHz
          capacity: 2GHz
          width: 32 bits
          clock: 166MHz
           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce  cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht  tm pbe nx constant_tsc bts aperfmperf pni monitor vmx est tm2 xtpr pdcm  dtherm cpufreq
          configuration: id=0
        *-cache:0
             description: L2 cache
             physical id: 11d
             slot: Unknown
             size: 2MiB
             capacity: 2MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 11f
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-cache:0
          description: L1 cache
          physical id: 11e
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-cpu:1
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 120
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U2E1
          size: 1GHz
          capacity: 2GHz
          clock: 166MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-cache:0
             description: L2 cache
             physical id: 121
             slot: Unknown
             size: 2MiB
             capacity: 2MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 123
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-cache:1
          description: L1 cache
          physical id: 122
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-memory
          description: System Memory
          physical id: 124
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: M4 70T2953EZ3-CE6
             vendor: Samsung
             physical id: 0
             serial: 0x320E8AAA
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: M4 70T2953EZ3-CE6
             vendor: Samsung
             physical id: 1
             serial: 0x320E89E5
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:88300000-883fffff ioport:80000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: RV530/M56-P [Mobility Radeon X1600]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                 resources: irq:44 memory:80000000-87ffffff  ioport:2000(size=256) memory:88300000-8830ffff memory:88320000-8833ffff
        *-generic UNCLAIMED
             description: Performance counters
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:88404000-88404fff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:88400000-88403fff
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:88200000-882fffff ioport:88500000(size=2097152)
           *-network
                description: Ethernet interface
                product: 88E8053 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 22
                serial: 00:16:cb:c0:f4:92
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                 capabilities: pm vpd msi pciexpress bus_master cap_list  rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
                configuration: autonegotiation=on  broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=10.0.0.7  latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:43 memory:88200000-88203fff ioport:1000(size=256) memory:88220000-8823ffff
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:88100000-881fffff ioport:88700000(size=2097152)
           *-network
                description: Network controller
                product: BCM4311 802.11a/b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:17 memory:88100000-88103fff
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:30a0(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:3080(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:3060(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:3040(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:88405400-884057ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:88000000-880fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW322/323 [TrueFire] 1394a Controller
                vendor: LSI Corporation
                physical id: 3
                bus info: pci@0000:04:03.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=248 maxlatency=24 mingnt=12
                resources: irq:19 memory:88000000-88000fff
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
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:30c0(size=16)
        *-ide:1
             description: IDE interface
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
              resources: irq:19 ioport:30d8(size=8) ioport:30f4(size=4)  ioport:30d0(size=8) ioport:30f0(size=4) ioport:3020(size=16)  memory:88405000-884053ff
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:efa0(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD-R   UJ-846
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: FB2U
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=open
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Maxtor 6L250M0
             vendor: Maxtor
             physical id: 0.1.0
             bus info: scsi@2:0.1.0
             logical name: /dev/sda
             version: 1GE0
             serial: L59PWZRG
             size: 233GiB (251GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00001c17
           *-volume:0 UNCLAIMED
                description: EFI GPT partition
                physical id: 1
                bus info: scsi@2:0.1.0,1
                capacity: 200MiB
                capabilities: primary nofs
           *-volume:1
                description: Darwin/OS X HFS+ partition
                vendor: Mac OS X (journaled)
                physical id: 2
                bus info: scsi@2:0.1.0,2
                logical name: /dev/sda2
                version: 4
                serial: 026f7634-95b3-eca1-0000-00000074c000
                size: 69GiB
                capacity: 69GiB
                capabilities: primary bootable journaled osx hfsplus initialized
                 configuration: boot=osx checked=2011-10-07 11:11:43  created=2011-10-07 08:11:43 filesystem=hfsplus lastmountedby=HFSJ  modified=2015-09-03 18:29:11 state=clean
           *-volume:2
                description: Non-FS data partition
                physical id: 3
                bus info: scsi@2:0.1.0,3
                logical name: /dev/sda3
                capacity: 1MiB
                capabilities: primary nofs
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@2:0.1.0,4
                logical name: /dev/sda4
                logical name: /
                version: 1.0
                serial: 5337a4f8-138f-458d-9ffa-cc57a6bfa834
                size: 161GiB
                capacity: 161GiB
                 capabilities: primary journaled extended_attributes  large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                 configuration: created=2015-09-03 21:54:46  filesystem=ext4 lastmountpoint=/ modified=2015-09-07 18:39:12  mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro,data=ordered  mounted=2015-09-07 18:39:13 state=mounted
```

I am not sure what log to post, regarding suspend. The command "cat /sys/power/state" returns the following: "freeze mem disk"

I  note that the default, when running the IMac with OSX, is to suspend to  RAM if the computer has not been used for a set period of time. I think  the time is about 30 minutes. I am not sure this is particularly good  for the hard drive but, then again, Apple must have thought it a good  idea at some point; otherwise, the IMac would not be set to suspend  automatically.

One last thing. If I set the computer, using Mint,  to suspend via the power manager program, the machine will not suspend  and the screen will not turn off. Hence, I have set the computer not to  suspend automatically. As a result, the screen will turn off most of the time. The only time it does not turn off is when I first reboot and, I think, login after logging out. In that case, I open up Power Manager and move the "Switch off after" time - and then close the program. After that, the screen shuts off normally, at 8 minutes, as I have set it.

I assume this is primarily a hardware related issue, which is why I posted it here.

I realize that this is the Ubuntu, not Mint, forum but, be that as it may, any help or information would be very much appreciated.

---

### Post by howefield on 2015-09-23
Thread moved to the "*MINT*" forum.

---

### Post by nef1312 on 2015-09-23
While I understand the logic of moving this discussion to the Mint forum, I rather doubt the problem has anything to do with anything specific to Mint. Which is to say, had I installed Xubuntu, I would almost certainly be having the same problem.

---

### Post by trtle on 2015-09-28
I'm having the same problem,

I took a screenshot and it's clear as day

Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV610/M74 [Mobility Radeon HD 2400 XT] 
           X.Org: 1.15.1 driver: radeon Resolution: 1680x1050@59.9hz 
           GLX Renderer: Gallium 0.4 on AMD RV610 GLX Version: 3.0 Mesa 10.1.3

suspend says the from MDM log says
(II) AIGLX: Suspending AIGLX clients for VT switch

But it all seems to look like it's because it's missing half the interlace
The interlace isn't working or it's trying to interlace or otherwise interleave

I know cause your complaint got me to thinking I could install this onto my iMac
And the bug is definitely replicated!

---

### Post by nef1312 on 2015-10-01
I like your thinking. Maybe, there is a package which is missing.

---

