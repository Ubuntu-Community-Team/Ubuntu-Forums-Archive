---
title: "upgrade 8.04 to 10.04 fail live CD fail"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by bojo on 2010-12-27
Hi All,

Few days ago I tried upgrade to 10.04 LTS and the behavior was that the screen freezes to the point that I couldn't login at all (list of users barely appeared but can not navigate to a user). I did restore back to 8.04 using clonezilla and tried live CD. What I experienced is the same on Live CD 10.04 32 bit, Live CD 10.10 32 bit and a bit better (I was able to login and navigate however with some slowness on 10.04 64 bit). I know my video card is about 10 years old but it works just fine with 8.04 and all previous versions that I used.

I am wandering if there is a way to make any of the 32 bit versions work. I'd rather experiment with the live CD as I don't want to risk the system before I am sure I can actually make it work. 

One more test - I tried running live CD in a session of virtual box (within the 8.04 32 bit system) and it is OK...

Any ideas? Suggestions? If I can't make it work one way or another I am stuck (can't upgrade and no security updates after that). I didn't try 9.10 as support will run out about the same time as 8.04.

Thank you in advance...

Here is the data for the machine

```

lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x T

lspci

00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
02:07.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
02:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)


```

All the hardware below

```

sudo lshw

    description: Desktop Computer
    product: K8N
    vendor: ASUSTek Computer Inc.
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.1 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=208658BB-8DFE-D511-A9B3-0013D4E3C73E
  *-core
       description: Motherboard
       product: 'K8N'
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1008 (08/23/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 2800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.0
          serial: To Be Filled By O.E.M.
          slot: Socket 754
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up ts fid vid ttp
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-cache DISABLED
          description: L3 cache
          physical id: 7
          slot: L3-Cache
          clock: 3921KHz (255.0ns)
          capabilities: internal
     *-memory
          description: System Memory
          physical id: 3a
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
     *-pci:0
          description: Host bridge
          product: nForce3 250Gb Host Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz
        *-isa
             description: ISA bridge
             product: nForce3 250Gb LPC Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce 250Gb PCI System Management
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
        *-usb:0
             description: USB Controller
             product: CK8S USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.24-28-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=4 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: CK8S USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.24-28-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=4 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: USB Trackball
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@2:2
                   version: 14.00
                   capabilities: usb-1.10
                   configuration: maxpower=50mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: nForce3 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.24-28-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: maxpower=0mA slots=8 speed=480.0MB/s
        *-bridge
             description: Ethernet interface
             product: CK8S Ethernet Controller
             vendor: nVidia Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: eth0
             version: a2
             serial: 00:13:d4:e3:c7:3e
             size: 100000000
             capacity: 100000000
             width: 32 bits
             clock: 66MHz
             capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=172.16.30.52 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
        *-ide:0
             description: IDE interface
             product: CK8S Parallel ATA Controller (v2.5)
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             logical name: scsi1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
           *-cdrom
                description: DVD writer
                product: DVD_RW ND-3540A
                vendor: _NEC
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.01
                serial: [_NEC    DVD_RW ND-3540A 1.0105031600
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: CK8S Serial ATA Controller (v2.5)
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: scsi2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
           *-disk
                description: ATA Disk
                product: Maxtor 6L250S0
                vendor: Maxtor
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: BANC
                serial: L5090XLG
                size: 233GiB (251GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0000e20b
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 188MiB
                   capabilities: primary
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 1.0
                   serial: bf95d643-5c58-431c-8fa5-bae6ba4d7eab
                   size: 188MiB
                   capacity: 188MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: filesystem=ext3 modified=2010-12-22 15:32:08 mounted=2010-12-22 15:32:08 state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   size: 231GiB
                   capacity: 231GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 27GiB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1906MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /home
                      capacity: 93GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,data=ordered state=mounted
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      logical name: /home/back_vm
                      capacity: 81GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,data=ordered state=mounted
                 *-logicalvolume:4
                      description: Linux filesystem partition
                      physical id: 9
                      logical name: /dev/sda9
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 27GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-volume:3
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /boot
                   version: 1.0
                   serial: c73148b2-3a22-437c-8e17-eecc87489233
                   size: 188MiB
                   capacity: 188MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-10-12 13:10:15 filesystem=ext3 modified=2010-12-27 10:31:21 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2010-12-27 10:31:21 state=mounted
        *-pci:0
             description: PCI bridge
             product: nForce3 250Gb AGP Host to PCI Bridge
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Rage 128 PF/PRO AGP 4x TMDS
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=64 mingnt=8
        *-pci:1
             description: PCI bridge
             product: nForce3 250Gb PCI-to-PCI Bridge
             vendor: nVidia Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-communication UNCLAIMED
                description: Communication controller
                product: HCF 56k Data/Fax/Voice/Spkp Modem
                vendor: Conexant
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 9
                bus info: pci@0000:02:09.0
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: 9.1
                bus info: pci@0000:02:09.1
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=64 module=emu10k1_gp
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes



```

---

