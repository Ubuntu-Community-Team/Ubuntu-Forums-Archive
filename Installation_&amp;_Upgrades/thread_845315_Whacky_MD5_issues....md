---
title: "Whacky MD5 issues..."
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by lionstone on 2008-06-30
Hi, I'm encountering a bizarre problem.

I have been trying to install hardy 64-bit. I downloaded, checked the md5 of the ISO, and burned to CD. Ran the "check CD integrity" option at boot, and it alerted "check finished: errors found in 1 files!" 

OK, so I checked the MD5 of the whole burned CD. No problems. I said, "huh, maybe it was the actual file from the mirror?" So I downloaded another ISO, burned it ( 2x speed )...and same problem. Finally, my friend downloaded another ISO from a different mirror, burned it, and checked the CD on his computer. It validated no problem. Of course, I try using the very same CD i my machine and continue to get the same error "check finished: errors found in 1 files!"

So I say alright, maybe it's my CD-ROM drive. I went out and got an external USB CD drive, boot off it...and still, same exact problems. 

A little more info: I also tried downloading and installing an alternative version of the installer (Ubuntu Studio 64-bit) It actually displayed the file that failed validation, which was something like console-installer.deb  

That seems to make sense, because the one time I tried to actually install, it hung up on the partitioner.

At this point I'm at a total loss here. Here are my hardware specs (printed with lshw):

```
   
    description: Desktop Computer
    product: MS-7125
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    version: 1.0
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: MS-7125
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: 1.0
       slot: E
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (09/09/2005)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3000+
          slot: Socket 939
          size: 1810MHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-back
     *-cpu:1 DISABLED
          description: CPU
          vendor: Unknown
          physical id: 5
          bus info: cpu@1
          version: AMD Athlon(tm) 64 Processor 3000+
          slot: Socket 939
          size: 1810MHz
          capacity: 3GHz
          clock: 201MHz
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             width: 64 bits
        *-bank:2
             description: DIMM
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GB
             width: 64 bits
        *-bank:3
             description: DIMM
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 1GB
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: f2
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
           *-cdrom
                description: DVD writer
                product: SONY DVD RW DW-Q30A
                physical id: 1
                bus info: ide@0.1
                logical name: /dev/hdb
                version: YYS1
                capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                configuration: status=nodisc
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: scsi0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: SCSI Disk
             product: Maxtor 6Y120M0
             vendor: ATA
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: YAR5
             serial: Y3MCRPZE
             size: 114GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume:0
                description: Linux filesystem partition
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                capacity: 109GB
                capabilities: primary bootable
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 4800MB
                capacity: 4800MB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 4800MB
                   capabilities: nofs
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi3
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: SCSI Disk
             product: Maxtor 7H500F0
             vendor: ATA
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: HA43
             serial: H812LH6H
             size: 465GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume
                description: Linux filesystem partition
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                capacity: 465GB
                capabilities: primary
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: 8
             bus info: pci@0000:01:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a3
          serial: 00:13:d3:9c:fa:93
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.1.106 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display:0
             description: VGA compatible controller
             product: RV370 5B60 [Radeon X300 (PCIE)]
             vendor: ATI Technologies Inc
             physical id: 0
             bus info: pci@0000:05:00.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga bus_master cap_list
             configuration: driver=fglrx_pci latency=0 module=fglrx
        *-display:1 UNCLAIMED
             description: Display controller
             product: RV370 [Radeon X300SE]
             vendor: ATI Technologies Inc
             physical id: 0.1
             bus info: pci@0000:05:00.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress cap_list
             configuration: latency=0
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp



```

---

### Post by dstew on 2008-06-30
So, the CD that validated in your friend's computer (ran CD integrity and it had no errors) in your computer, has an error?

Possibilities that come to mind are:

--A weak burn with some marginally visible bits, that one drive can see, but another cannot.

--A bug in the software of the kernel in the CD that gives a problem with your hardware, but not your friend's.

I assume the md5 sum you got from the CD and .iso were both the same, and were what they were supposed to be. I think the .iso software behaves differently than the CD integrity check software, and so they might give conflicting results. It is possible that the CD integrity check looks at the file system structure, and also counts the bits. If the bit-count is correct, there still could be a disk error if a sector or track was burned a little off-center, or has a gap or overlap that interfers with proper timing. But, I am just guessing about that.

---

### Post by lionstone on 2008-06-30
Hey, thanks for the response dstew!

At this point, I am fairly convinced that the ISOs are intact. There were numerous ISOs tried, downloaded from different mirrors onto different computers, and burned with different CD drives. They all gave me the same error, while they validate fine on my buddy's machine.

I doubt the problem would be a weak burn, seeing as there were different CD burners used.

I'm more curious about the possibility that there is a conflict between the kernal of the CD and my hardware. Any suggestions how I can test this / possible workarounds?  My hardware may indeed be flaky, as I occasionally get weird things going on (ie- 1 out of 100 times i turn the machine on, it will freeze at the GDM login screen, and all three lights on the keyboard will be flashing. )

But I had previously installed Ubuntu onto the same machine with no problems like this.

---

### Post by SkonesMickLoud on 2008-06-30
If you're attempting to install 8.04, you could try to install 7.10 and then dist-upgrade.

---

### Post by lionstone on 2008-06-30
Hi SkonesMickLoud, and thanks for the suggestion. 

Yes, I am trying to install 8.04, and yes, I am currently running 7.10. However, I need to install onto a different hard drive, so dist-upgrade won't do it, right? 

Also, I could really use a fresh install, a little belated spring cleaning :)

---

### Post by jnewm on 2009-01-25
Hi all,

I just wanted to see if you ever figured anything out.  It seems like your problem is a bit like mine (see [http://ubuntuforums.org/showthread.php?p=6613542#post6613542](http://ubuntuforums.org/showthread.php?p=6613542#post6613542)).  Although I'm not sure if your md5sum/integrity check issues carried across ubuntu/linux versions...

---

