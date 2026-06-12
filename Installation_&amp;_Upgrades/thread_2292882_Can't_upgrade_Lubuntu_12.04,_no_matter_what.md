---
title: "Can't upgrade Lubuntu 12.04, no matter what"
date: 2015-08-31
forum: Installation &amp; Upgrades
---

### Post by CM224 on 2015-08-31
Hi, I've been running Lubuntu 12.04 on a old HP Windows Vista PC for 4 months now and it has been an amazing run so far. However, I do realize that Ubuntu 12.04 is about 3 years old, so I'd like to upgrade. I downloaded the LTS Lubuntu 14.04 iso and checked the md5sum, so I know for a fact it has nothing to do with the ISO. So I used Startup Disk Creator to make a Live USB so I could install it on my PC. I went in my BIOS and booted it successfully, but got numerous Black screens and a message on my monitor saying: "NO SUPPORT". I believe this is because of resolution issues but the card outputs 1024x768 on my Lubuntu 12.04 system, so I dont understand why this is happening. I set it to "nomodeset", put in "xforcevesa", tried the other acpi F6 settings as well: but still got the same message. Please help, I really want to upgrade, this has been my 3rd attempt now.
by the way my graphics card is ancient :p, but Lubuntu perfectly recognizes it on my 12.04 OS :
Sillicon Integrated Systems [SiS] 86C326 5598/6326 (rev 0b)

---

### Post by mörgæs on 2015-08-31
Hi, welcome to the fora.

SIS could be a problem. Let's see more hardware details, please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by CM224 on 2015-08-31
Thanks much man for the welcome ):P
```
computer    description: Desktop Computer
    version: 1111
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2
  *-core
       description: Motherboard
       product: NODUSM3
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.05
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 5.04
          date: 12/15/2006
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 1
          bus info: cpu@0
          version: 15.11.2
          slot: Socket AM2
          size: 2400MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy vmmcall cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: b
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 11
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 0
             serial: [REMOVED]
             slot: A0
             width: 64 bits
        *-bank:1
             description: DIMM DDR2 533 MHz (1.9 ns)
             product: None
             vendor: None
             physical id: 1
             serial: [REMOVED]
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: [REMOVED]
             slot: A2
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: [REMOVED]
             slot: A3
             width: 64 bits
     *-cpu:1
          physical id: 3
          bus info: cpu@1
          version: 15.11.2
          size: 2400MHz
          capacity: 2400MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: NVIDIA Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: NVIDIA Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: NVIDIA Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: NVIDIA Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: NVIDIA Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: NVIDIA Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:b000(size=4096) memory:fdd00000-fddfffff ioport:fdb00000(size=1048576)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 ioport:9000(size=4096) memory:fda00000-fdafffff ioport:fde00000(size=1048576)
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: NVIDIA Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:7 ioport:4c00(size=64) ioport:4c40(size=64)
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: NVIDIA Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP51 USB Controller
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB controller
          product: MCP51 USB Controller
          vendor: NVIDIA Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02e000-fe02e0ff
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f400(size=16)
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          logical name: scsi2
          logical name: scsi3
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:e000(size=16) memory:fe02d000-fe02dfff
        *-disk
             description: ATA Disk
             product: ST3320820AS
             vendor: Seagate
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 3.AH
             serial: [REMOVED]
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000787e8
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 297GiB
                capacity: 297GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-06-22 16:17:59 filesystem=ext4 lastmountpoint=/ modified=2015-08-31 16:07:42 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2015-08-31 17:59:13 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 1022MiB
                capacity: 1022MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1022MiB
                   capabilities: nofs
        *-cdrom
             description: DVD-RAM writer
             product: CD/DVDW TS-H653L
             vendor: TSSTcorp
             physical id: 1
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 0414
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-ide:2
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:cc00(size=16) memory:fe02c000-fe02cfff
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: NVIDIA Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:a000(size=4096) memory:fdc00000-fdcfffff memory:fd000000-fd7fffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: FW322/323 [TrueFire] 1394a Controller
             vendor: LSI Corporation
             physical id: 5
             bus info: pci@0000:03:05.0
             version: 70
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=24 mingnt=12
             resources: irq:19 memory:fdcff000-fdcfffff
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 86C326 5598/6326
             vendor: Silicon Integrated Systems [SiS]
             physical id: 8
             bus info: pci@0000:03:08.0
             version: 0b
             width: 32 bits
             clock: 66MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: latency=32 mingnt=2
             resources: memory:fd000000-fd7fffff memory:fdce0000-fdceffff ioport:ac00(size=128) memory:fdcc0000-fdccffff
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax Modem
             vendor: Conexant Systems, Inc.
             physical id: 9
             bus info: pci@0000:03:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
             resources: memory:fdcd0000-fdcdffff ioport:a800(size=8)
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:fe024000-fe027fff
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: NVIDIA Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: [REMOVED]
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=[REMOVED] latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:23 memory:fe02b000-fe02bfff ioport:c800(size=8)
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 5
          bus info: usb@1:3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             size: 15GiB (16GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=0008af4e
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/BFCC-B457
                version: FAT32
                serial: [REMOVED]
                size: 15GiB
                capacity: 15GiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
     *-scsi:1
          physical id: 6
          bus info: usb@1:8
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@7:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@7:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@7:0.0.3
             logical name: /dev/sdf

```

---

### Post by sudodus on 2015-09-01
While waiting for a reply from *mörgæs*, who knows better than I, if the problem is the SIS graphics, you can try

Bento, Bodhi, LXLE or ToriOS,

which are also based on Ubuntu 12.04 LTS, but with updated program packages and a promise of support until April 2017. (Lubuntu 12.04 has passed end of life).

---

### Post by mörgæs on 2015-09-01
Thanks :-)

It is indeed an old graphics card. Even if it worked I would suggest to replace it by a younger Nvidia card which fits the slot.

I don't know the card but SIS has made trouble before. As a first attempt, have you tried the [alternate Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")? Else the suggestions above are worth trying.

---

### Post by CM224 on 2015-09-01
Thank you guys for the support, I'll be trying out one of those operating systems with a Live USB. I searched some stuff on SiS support in 14.04, and I realized the card wasnt' really supported.

---

### Post by sudodus on 2015-09-01
> **CM224 said:**
> Thank you guys for the support, I'll be trying out one of those operating systems with a Live USB. I searched some stuff on SiS support in 14.04, and I realized the card wasnt' really supported.

Yes, it's a good idea to try them live before installing :-)

---

### Post by CM224 on 2015-09-01
Mark this as solved folks, LXLE is a keeper! ;)

---

### Post by mörgæs on 2015-09-01
Good, please see Thread Tools.

---

