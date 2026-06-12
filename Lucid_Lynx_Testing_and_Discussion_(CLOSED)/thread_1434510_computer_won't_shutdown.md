---
title: "computer won't shutdown"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mick222 on 2010-03-20
Strange problem.Since the beta cane out my computer won't shutdown. Ubuntu closes but my fans keep running anybody have a clue whats happening.

---

### Post by lavinog on 2010-03-20
> **mick222 said:**
> Strange problem.Since the beta cane out my computer won't shutdown. Ubuntu closes but my fans keep running anybody have a clue whats happening.

What did you update from?
How did you update?
What are your system specs?
can you post lshw, dmesg, lspci?

---

### Post by mick222 on 2010-03-20
I have been running lucid since alpha 1 and updated using update manager
[PHP] description: Desktop Computer
    product: K8S8X
    vendor: TBD
    version: 1.00
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: K8S8X
       vendor: TBD
       physical id: 0
       version: 1.00
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.50 (02/23/2004)
          size: 64KiB
          capacity: 192KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.0
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System memory
          physical id: 1
          size: 1015MiB
     *-pci:0
          description: Host bridge
          product: 755 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-amd64 latency=32
          resources: irq:0 memory:e0000000-e1ffffff
        *-pci
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:b000(size=4096) memory:fea00000-feafffff memory:9ff00000-dfefffff(prefetchable)
           *-display:0
                description: VGA compatible controller
                product: RV350 AP [Radeon 9600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm bus_master cap_list rom
                configuration: driver=radeon latency=64 mingnt=8
                resources: irq:16 memory:c0000000-cfffffff(prefetchable) ioport:b800(size=256) memory:feaf0000-feafffff memory:feac0000-feadffff(prefetchable)
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 AP [Radeon 9600] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: memory:b0000000-bfffffff(prefetchable) memory:feae0000-feaeffff
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
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
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-disk
                description: ATA Disk
                product: Maxtor 6Y080L0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: YAR4
                serial: Y30MQK7E
                size: 76GiB (81GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=4fc94fc8
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: 0b082978-bdc9-40be-93a5-d05f84683afe
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-01-11 21:25:20 filesystem=ext4 label=suse lastmountpoint=/rooto>H~&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@m&#65533;&#65533;&#65533;^&#65533;&#65533;#1&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;o>H~&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^&#65533;&#65533;^ modified=2010-03-14 15:08:38 mounted=2010-03-14 13:38:54 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sdb2
                   size: 63GiB
                   capacity: 63GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 63GiB
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sdb3
                   version: 1
                   serial: 55d7e191-f3cd-41e1-bdc0-f9d8c00e63ad
                   size: 2133MiB
                   capacity: 2133MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom
                description: DVD-RAM writer
                product: DVD_RW ND-4551A
                vendor: _NEC
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1-84
                serial: [_NEC    DVD_RW ND-4551A 1-8405092800
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52
             resources: irq:18 ioport:d000(size=256) ioport:cc00(size=128)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:20 memory:febf9000-febf9fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:21 memory:febfa000-febfafff
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:22 memory:febfb000-febfbfff
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:23 memory:febfc000-febfcfff
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 90
             serial: 00:0b:6a:4e:f7:1c
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.0.102 latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
             resources: irq:19 ioport:d400(size=256) memory:febfd000-febfdfff memory:40000000-4001ffff(prefetchable)
        *-storage
             description: RAID bus controller
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=sata_sis latency=128
             resources: irq:17 ioport:ec00(size=8) ioport:e800(size=4) ioport:e400(size=8) ioport:e000(size=4) ioport:dc00(size=16) ioport:d800(size=128)
           *-disk
                description: ATA Disk
                product: WDC WD1600JS-55N
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 10.0
                serial: WD-WCANM2051742
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=4b730ade
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 5072b521-fc32-4644-b84a-12fb46e35402
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-01-10 16:15:15 filesystem=ext4 label=lucid lastmountpoint=/V&#65533;&#65533;&#65533;&#65533;2&#65533;&#526;&#65533;&#65533;&#65533;&#65533;2&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;6 &#65533;]'/&#65533;&#65533;&#65533;&#65533;n&#65533; &#65533;hO&#65533;&#65533;hO&#65533;&#65533;&#65533;2&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;=9 modified=2010-03-18 07:27:04 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-03-20 15:14:46 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 34452103-dc7e-9342-b158-fe2b652a2505
                   size: 51GiB
                   capacity: 51GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2006-06-11 16:16:44 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 10GiB
                   capacity: 10GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5679MiB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 666MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 4612MiB
              *-volume:3
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /home
                   version: 1.0
                   serial: c322e42d-6c17-497e-aeea-6716d59cdd92
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-01-10 16:15:53 filesystem=ext4 label=lucid home lastmountpoint=/home&#65533;&#65533;_&#65533;.C&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;B&#65533;6 &#65533;&#65533;&#65533;B&#65533;&#65533;B&#65533;H&#65533;X>N&#65533;X>N&#65533;.C&#65533;&#65533;&#65533;&#65533;&#65533;B&#65533; modified=2010-03-20 15:14:46 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2010-03-20 15:14:46 state=mounted
        *-network:1
             description: Wireless interface
             product: RT2500 802.11g Cardbus/mini-PCI
             vendor: RaLink
             physical id: c
             bus info: pci@0000:00:0c.0
             logical name: wlan0
             version: 01
             serial: 00:02:44:aa:f3:3c
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rt2500pci ip=192.168.0.104 latency=64 multicast=yes wireless=IEEE 802.11bg
             resources: irq:16 memory:febfe000-febfffff
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
          configuration: driver=k8temp
          resources: irq:0

[/PHP]
[PHP]00:00.0 Host bridge: Silicon Integrated Systems [SiS] 755 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0c.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
[/PHP]
dmesg just gives an error with a wireless card that i don't use .which is not new and hasn't caused problems in the past.

---

### Post by lavinog on 2010-03-20
Does the problem occur if you go into recovery mode then shutdown?

Also, have you checked to see if there is a bios update for your computer? it shows 2/23/2004...usually manufacturers have something more recent even for older computers.

---

### Post by mick222 on 2010-03-20
The last bios update was in 2005 I only apply them if I am having problems.Ill try starting in recovery mode and shutting down from there ,but don't see why it would make a difference.Thx

---

### Post by wilee-nilee on 2010-03-20
How are you shutting it down and have you checked if that method makes it hibernate, rather then shut down. there is a shutdown and reboot command that is good to know.
[http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub)
reisub=reboot reisuo=shutdown

---

### Post by mick222 on 2010-03-20
> How are you shutting it down and have you checked if that method makes it hibernate, rather then shut down. there is a shutdown and reboot command that is good to know.
[http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub)
reisub=reboot reisuo=shutdown
have tried reisub which worked reboot from the menu also works reisuo seemed to shutdown but hung at some point leaving the cpu running ,the same as from menu. Tried using terminal; "shutdown -v now " thought the -v might give more info, It stuck at the Ubuntu splash screen.Strangely won't start in recovery mode will try using another kernel as it was ok a few days ago.
Tried another kernel also tried using Suse 11 ,which i'd almost forgotten about,It must be a hardware problem as it happens with them all no matter how i shutdown will reset bios and see if that will help.

---

### Post by dmegg on 2010-03-28
I have exactly the same problem with 64-bit Lucid -- it runs through the whole shutdown sequence, but then freezes at the end (all dots red) without actually turning off my HP TouchSmart tx2 notebook.  The problem did not exist with 64-bit Jaunty on the same hardware.

---

### Post by lavinog on 2010-03-28
I thought I saw something in the changelogs about fixing issues with fans...do the fans still run constantly?

---

### Post by zika on 2010-03-28
[http://ubuntuforums.org/showthread.php?t=1422189](http://ubuntuforums.org/showthread.php?t=1422189)

And still no shutdown... I've, even, rewired my system so that I have an external switch after AVR...

---

### Post by mick222 on 2010-03-30
thx at least i'm not alone but can't understand why it's happening with older kernals that used to work fine and also with suse.Will have to abandon lucid if this doesn't get fixed.

---

