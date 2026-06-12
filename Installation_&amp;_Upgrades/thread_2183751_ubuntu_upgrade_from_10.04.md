---
title: "ubuntu upgrade from 10.04"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by mavmic on 2013-10-26
Hello everybody

my hp laptop has radeon ati graphics card (nice) and installing the first versions of ubuntu 12  was a kind of a nightmare. finally a gave up and settled with the 10.04 version  which is quite good and very stable although i had my troubles with wireless drivers and  audio. i have a dual boot installation  with windows 7. my original installation was made with wubi from windows. i know that i could make a fresh installation (erasing everything after saving my data and use wubi again) of ubuntu newest stable version but i would like to ask some questions first :
can an upgrade be done without loosing data from inside ubuntu 10 ( it provides an upgrade to 12.04.03 and i guess then 13.0 will be provided) ? if i choose to upgrade with update manager will i lose my data and applications ?
do these new versions of ubuntu (12.04 , 13) support ati radeon graphics cards or do i have to download the drivers and install them manually as i am doing now ?

i hope i am expressing the above correctly.
Thanks in advance.
Best regards 
Mihalis

---

### Post by mörgæs on 2013-10-26
Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by mavmic on 2013-10-26
the output file i get
```
 computer
    description: Notebook
    product: HP Pavilion dv6 Notebook PC
    vendor: Hewlett-Packard
    version: 058F110000244610000620100
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=B121418C-B896-81F6-1F80-2C27D7ADE4FE
  *-core
       description: Motherboard
       product: 358D
       vendor: Hewlett-Packard
       physical id: 0
       version: 33.12
       serial: [REMOVED]
       slot: Base Board Chassis Location
     *-memory
          description: System Memory
          physical id: 0
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: SODIMM Synchronous 1334 MHz (0.7 ns)
             product: M471B5273DH0-CH9
             vendor: Samsung
             physical id: 0
             serial: [REMOVED]
             slot: DIMM1
             size: 4GiB
             width: 8 bits
             clock: 1334MHz (0.7ns)
        *-bank:1
             description: SODIMM Synchronous 1334 MHz (0.7 ns)
             product: NT2GC64B88B0NS-CG
             vendor: Nanya Technology
             physical id: 1
             serial: [REMOVED]
             slot: DIMM2
             size: 2GiB
             width: 8 bits
             clock: 1334MHz (0.7ns)
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 9
          version: F.1C (05/12/2011)
          size: 128KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: AMD A6-3410MX APU with Radeon(tm) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 14
          bus info: cpu@0
          version: AMD A6-3410MX APU with Radeon(tm) HD Graphics
          serial: [REMOVED]
          slot: Socket FS1
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpufreq
        *-cache:0
             description: L1 cache
             physical id: 15
             slot: L1 Cache
             size: 512KiB
             capacity: 512KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 16
             slot: L2 Cache
             size: 4MiB
             capacity: 4MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-pci:0
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-display
             description: VGA compatible controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list rom
             configuration: driver=fglrx_pci latency=0
             resources: irq:30 memory:d0000000-dfffffff(prefetchable) ioport:4000(size=256) memory:f0400000-f043ffff
        *-multimedia:0
             description: Audio device
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:19 memory:f0444000-f0447fff
        *-pci:0
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:f0300000-f03fffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:31 memory:e0000000-efffffff(prefetchable) memory:f0300000-f031ffff ioport:3000(size=256) memory:f0320000-f033ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 06
                serial: [REMOVED]
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:29 ioport:2000(size=256) memory:f0004000-f0004fff(prefetchable) memory:f0000000-f0003fff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:f0200000-f02fffff
           *-network
                description: Wireless interface
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=[REMOVED] latency=0 multicast=yes wireless=IEEE 802.11
                resources: irq:17 memory:f0200000-f0203fff
        *-pci:3
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 memory:f0100000-f01fffff
           *-generic UNCLAIMED
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f0100000-f0100fff
        *-usb:0
             description: USB Controller
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:f0448000-f0449fff
        *-usb:1
             description: USB Controller
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:17 memory:f044a000-f044bfff
        *-storage
             description: SATA controller
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:28 ioport:4138(size=8) ioport:414c(size=4) ioport:4130(size=8) ioport:4148(size=4) ioport:4110(size=16) memory:f0450000-f04507ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54757
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: JE4O
                serial: [REMOVED]
                size: 698GiB (750GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=4f0ec774
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/SYSTEM
                   version: 3.1
                   serial: [REMOVED]
                   size: 197MiB
                   capacity: 199MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2012-09-18 22:53:43 filesystem=ntfs label=SYSTEM mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /host
                   version: 3.1
                   serial: [REMOVED]
                   size: 582GiB
                   capacity: 582GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-09-18 21:35:11 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 116GiB
                   capacity: 116GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /media/LINUX
                      capacity: 101GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 14GiB
                 *-logicalvolume:2
                      description: W95 FAT32 partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 102MiB
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ8B1
                vendor: hp
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: H.02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:2
             description: USB Controller
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:f044f000-f044ffff
        *-usb:3
             description: USB Controller
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:f044e000-f044e0ff
        *-usb:4
             description: USB Controller
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:f044d000-f044dfff
        *-usb:5
             description: USB Controller
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:f044c000-f044c0ff
        *-serial UNCLAIMED
             description: SMBus
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 13
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-ide
             description: IDE interface
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=32
             resources: irq:17 ioport:4128(size=8) ioport:4144(size=4) ioport:4120(size=8) ioport:4140(size=4) ioport:4100(size=16)
        *-multimedia:1
             description: Audio device
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:f0440000-f0443fff
        *-isa
             description: ISA bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
     *-pci:1
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 43
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 107
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 108
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz 
```

---

### Post by mörgæs on 2013-10-26
You have very powerful hardware and should be able to run any Buntu version without problems.

Wubi is a dead-end, and I recommend 13.10 in a classical dual (or triple) boot. Having two Buntus side by side gives you the option of moving slowly to the new one.

I don't know how support for Radeon graphics is.

---

### Post by fantab on 2013-10-26
> **mavmic said:**
> 
my hp laptop has radeon ati graphics card (nice) and installing the first versions of ubuntu 12  was a kind of a nightmare. finally a gave up and settled with the 10.04 version  which is quite good and very stable although i had my troubles with wireless drivers and  audio. i have a dual boot installation  with windows 7. my original installation was made with wubi from windows. i know that i could make a fresh installation (erasing everything after saving my data and use wubi again) of ubuntu newest stable version but i would like to ask some questions first :
can an upgrade be done without loosing data from inside ubuntu 10 ( it provides an upgrade to 12.04.03 and i guess then 13.0 will be provided) ? if i choose to upgrade with update manager will i lose my data and applications ?
do these new versions of ubuntu (12.04 , 13) support ati radeon graphics cards or do i have to download the drivers and install them manually as i am doing now ?

Like mörgæs said, "Wubi is a dead-end". You have to do a 'true' dual boot, that is, install Ubuntu separately from Windows to its own dedicated partition as a full install. But first, BACK UP all the important DATA you have saved in Wubi-Ubuntu then [Uninstall wubi.]("https://wiki.ubuntu.com/WubiGuide#Uninstallation")

Install Ubuntu 13.10. Note that you can have only four Primary Partitions. HP usually has all 4 Primary Partitions used up. So we may have to delete any one partition and create an Extended Partition. If you are unsure, post the output of the following commands from Ubuntu's Terminal:
```
sudo fdisk -l
sudo parted -l
```

---

### Post by mavmic on 2013-10-28
Thank you for your answers. 
It is true that i have deleted a partition that hp creates in order to install ubuntu. that is a great problem indeed. i have done this in the past so i know about it . I thank you also for the suggestions, especially booting more than two different systems which i was unaware off.  When i first tried to install ubuntu 12 i had a problem with the radeon ati graphics card drivers. i got a black screen but in the background installation was proceeding (i could here the sounds of the login screen). i thought the problem was with the default drivers for ati cards that ubuntu uses. i went with the 10.04 version because it gives you the choice to start in low graphics mode (no black screens there) so i was able to download and install the ati linux graphics drivers and everything worked.  Do the new 12.04 and 13.04 versions have such problems with the default ati drivers that ubuntu uses ? Can you start in low graphics mode or  black screens appear ? has anyone had such a problem

Best regards

---

### Post by fantab on 2013-10-28
> **mavmic said:**
> Thank you for your answers. 
It is true that i have deleted a partition that hp creates in order to install ubuntu. that is a great problem indeed. i have done this in the past so i know about it . I thank you also for the suggestions, especially booting different systems which i was unaware off.  When i first tried to install ubuntu 12 i had a problem with the radeon ati graphics card drivers. i got a black screen but in the background installation was proceeding (i could here the sounds of the login screen). i thought the problem was with the default drivers for ati cards that ubuntu uses. i went with the 10.04 version because it gives you the choice to start in low graphics mode (no black screens there) so i was able to download and install the ati graphics drivers and everything worked.  Do the new 12.04 and 13.04 versions have such problems with the default ati drivers that ubuntu uses ? Can you start in low graphics mode or  black screens appear ? has anyone had such a problem

Best regards

If you see the 'Black Screen' the use '[NOMODEST]("http://ubuntuforums.org/showthread.php?t=1613132")' option. 
The problem is not with Linux or Ubuntu, its with 'proprietory' drivers. NOMODESET boots Ubuntu in a "low graphics mode", that is, it uses basic, generic opensource graphic driver.

---

### Post by mavmic on 2013-10-28
Thank you [**[COLOR=#000000]fantab [/COLOR]**]("http://ubuntuforums.org/member.php?u=1275004")for your quick replay.
i cannot remember if i even got the screen in your link or it started black. anyway i consider this an option that i will try. i will try to make a third boot with a 13 version. thank you for your suggestions and help. i consider this post is solved
best regards mihalis

---

