---
title: "No partitions detected during Install of 8.04"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Zenkai on 2008-04-27
Hi there,

I attempted to do an updated to 8.04 via the Admin updated, after reboot I got kicked into busybox, I booted into recovery mode and noticed an error with DMA and it suggested that I needed to upgrade my sr driver I think, the system seemed to be saying that my HD was very slow to respond. I tried gparted from the liveCD terminal and it didn't detect any partitions.

I tried changing the udma type in the bios but the CD install of hardy still refuses to see my disk. I reinstalled gusty from CD and it detects my disk and works without a hitch.

Any suggestions? I'm fairly new to linux so you may need to take it step by step.

Cheers
Zenk

p.s. System is a Compaq Presario 6092EA with a single 160GB HD, no other OS.

---

### Post by Pumalite on 2008-04-27
Some people have had success going to BIOS and changing AHCI or IDE to RAID.

---

### Post by Zenkai on 2008-04-27
The drive is an IDE WD1600 JB, I've tried changing the  Transfer mode from Max UDMA to PIO, I only have 2 PIO modes and 3 DMA modes.

No RAID onboard.

---

### Post by Pumalite on 2008-04-27
Burn a new CD. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 4x or less, on CD-R of good quality, check CD integrity before install.

---

### Post by Zenkai on 2008-04-27
Did that to start with, the CD has already been used to upgrade my laptop as well.

---

### Post by Pumalite on 2008-04-27
Post:
lshw

---

### Post by Zenkai on 2008-04-27
```
zenk-desktop              
    description: Desktop Computer
    product: Presario 6092EA
    vendor: Compaq
    serial: 4D26KXLHR0WP
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=C7EFDFB9-118D-BD11-A09C-CEA5519F6512
  *-core
       description: Motherboard
       product: 07D0h
       vendor: Compaq
       physical id: 0
       serial: 4D26KXLHR0WP
       slot: FDD1
     *-firmware
          description: BIOS
          vendor: Compaq
          physical id: 1
          version: 686Y4 v2.13 (05/20/2002)
          size: 128KB
          capacity: 448KB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2100+
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          version: 6.6.2
          slot: U13
          size: 1733MHz
          capacity: 2300MHz
          width: 32 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: Internal L1 Cache
             size: 128KB
             capacity: 128KB
             capabilities: burst internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: Cache L2
             size: 256KB
             capacity: 4MB
             capabilities: burst internal write-back data
     *-memory:0
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          capacity: 3GB
        *-bank:0
             description: DIMM SDRAM Synchronous 133 MHz (7.5 ns)
             product: M2U51264DS8HC3G-5T
             vendor: JEDEC ID:7F 7F 7F 0B 00 00 00 00
             physical id: 0
             serial: 76152280
             slot: DIMM1
             size: 512MB
             width: 64 bits
             clock: 133MHz (7.5ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 133 MHz (7.5 ns)
             product: M2U51264DS8HC3G-5T
             vendor: JEDEC ID:7F 7F 7F 0B 00 00 00 00
             physical id: 1
             serial: 751521A5
             slot: DIMM2
             size: 512MB
             width: 64 bits
             clock: 133MHz (7.5ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 21
          slot: System board or motherboard
          capacity: 512KB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: U27
             size: 512KB
             width: 4 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: nForce CPU bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b2
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia module=nvidia_agp
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce 220/420 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce 220/420 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: b2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: b2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: nForce ISA Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: c3
             width: 32 bits
             clock: 66MHz
             capabilities: isa ht bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce PCI System Management
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: c1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=amd756_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_amd756
        *-usb:0
             description: USB Controller
             product: nForce USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: c3
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: nForce USB Controller
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: c3
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-network
             description: Ethernet interface
             product: nForce Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: c2
             serial: 00:40:ca:2c:32:96
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.1.11 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
        *-multimedia
             description: Multimedia audio controller
             product: nForce Audio
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: c2
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
        *-pci:0
             description: PCI bridge
             product: nForce PCI-to-PCI bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: c2
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master
           *-multimedia:0
                description: Multimedia video controller
                product: Bt878 Video Capture
                vendor: Brooktree Corporation
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: vpd pm bus_master cap_list
                configuration: driver=bttv latency=66 maxlatency=40 mingnt=16 module=bttv
           *-multimedia:1 UNCLAIMED
                description: Multimedia controller
                product: Bt878 Audio Capture
                vendor: Brooktree Corporation
                physical id: 7.1
                bus info: pci@0000:02:07.1
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: vpd pm cap_list
                configuration: latency=66 maxlatency=255 mingnt=4
           *-communication UNCLAIMED
                description: Communication controller
                product: V.92 56K WinModem
                vendor: Agere Systems
                physical id: 8
                bus info: pci@0000:02:08.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=66 maxlatency=14 mingnt=252
        *-ide
             description: IDE interface
             product: nForce IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: c3
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3 module=amd74xx
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD1600JB-00EVA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 15.05R15
                   serial: WD-WMAEK2172681
                   size: 149GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 146GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 2870MB
                      capacity: 2870MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 2870MB
                         capabilities: nofs
        *-pci:1
             description: PCI bridge
             product: nForce AGP to PCI Bridge
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NVCrush11 [GeForce2 MX Integrated Graphics]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: b1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5

```

I think it might be easier to solve this problem if I do another update to heron via the update manager and then post the exact error I get during the boot sequence. Does that seem like a good idea?

Cheers
Zenk

---

### Post by Pumalite on 2008-04-27
The kernel is not recognizing a lot of stuff in your hardware.
(UNCLAIMED)

---

