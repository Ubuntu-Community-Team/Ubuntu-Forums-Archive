---
title: "LiveCD bios looping"
date: 2017-11-12
forum: Installation &amp; Upgrades
---

### Post by lnewlfe on 2017-11-12
I have an older computer, ran ubuntu 8, went to edubuntu 10, upgraded to 14. Started into login looping.... Long story short I screwed up desktop files, wont but up unless to root, but I got over this... Decided to reinstall lubuntu anyways, want the resources back.

/sda1 is windowsXP, /sdb1 is linux, grub has no issues with these. Dual booting is fine.

I just burned edubuntu liveCD 14, works no problem. Issue is with lubuntu. First iso i burned was 17.10, when it starts up, I get the quick flash across the screen showing the copyright info, then a split second latter it loops back to bios, starting process over. No splash screen. I then downloaded 16.04 lts, same issue. Disks work fine on my main, new computer that burned them, and yes I did proper burn. Any ideas why lubuntu liveCD is bios looping?

Bios is set to go cd 1, hd 2.

---

### Post by mörgæs on 2017-11-13
Hi, welcome to the fora.
Are you able to boot from USB?

---

### Post by lnewlfe on 2017-11-13
Computer bios is too old to allow it, just a floppy is allowed.

---

### Post by lnewlfe on 2017-11-13
Well an update, version 12.04 alt liveCD booted up no problem. Any ideas why this worked? something change from 12 to 16/17? or was it due to going with the alternate version?

---

### Post by mörgæs on 2017-11-14
The alternate ISO does not perform a live boot, it's only for installing. 

Let's see the hardware details. Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` into the terminal, run it and post lshw.txt in CODE tags. Can be done from an installed Buntu or a live boot.

---

### Post by lnewlfe on 2017-11-15
```
computer
    description: Mini Tower Computer
    product: -[848038X]-
    vendor: IBM
    version: IBM CORPORATION
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=mini-tower cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: -[M51G]-
       vendor: IBM
       physical id: 0
       version: -1
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: -[JPE150AUS-1.50]-
          date: 10/08/2004
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.7
          slot: CPU1
          size: 2400MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             slot: CPU1
             size: 8KiB
             capacity: 32KiB
             capabilities: internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 701
             slot: CPU1
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal write-back unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous
             physical id: 0
             slot: DIMM1
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous
             physical id: 1
             slot: DIMM2
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e0000000-e3ffffff
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:a000(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-98-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Keyboard
                   product: HP Basic USB Keyboard
                   vendor: Lite-On Technology Corp.
                   physical id: 2
                   bus info: usb@2:2
                   version: 1.04
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:a040(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-98-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:a2c00000-a2c003ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-98-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Belkin Components
                   physical id: 1
                   bus info: usb@1:1
                   version: 77.64
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb
                      description: Mouse
                      product: Gaming Mouse G300
                      vendor: Logitech
                      physical id: 2
                      bus info: usb@1:1.2
                      version: 70.02
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=200mA speed=12Mbit/s
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:7000(size=12288) memory:80a00000-a20fffff
           *-display:0
                description: VGA compatible controller
                product: NV34 [GeForce FX 5500]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
                resources: irq:16 memory:81000000-81ffffff memory:90000000-9fffffff memory:80a00000-80a1ffff
           *-network:0 UNCLAIMED
                description: Network controller
                product: RTL8190 802.11n PCI Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 maxlatency=64 mingnt=32
                resources: ioport:7000(size=256) memory:80a20000-80a20fff
           *-network:1
                description: Ethernet interface
                product: NetXtreme BCM5702X Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 66MHz
                capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5702-v2.37 ip=[REMOVED] latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:19 memory:80a30000-80a3ffff
           *-display:1 UNCLAIMED
                description: VGA compatible controller
                product: Rage XL PCI
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 27
                width: 32 bits
                clock: 33MHz
                capabilities: pm vga_controller cap_list
                configuration: latency=32 mingnt=8
                resources: memory:a1000000-a1ffffff ioport:9000(size=256) memory:a0400000-a0400fff memory:a0420000-a043ffff
           *-scsi
                description: SCSI storage controller
                product: AIC-7892P U160/m
                vendor: Adaptec
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: scsi2
                version: 02
                width: 64 bits
                clock: 66MHz
                capabilities: scsi pm bus_master cap_list rom scsi-host
                configuration: driver=aic7xxx latency=32 maxlatency=25 mingnt=40
                resources: irq:22 ioport:7800(size=256) memory:80a22000-80a22fff memory:80a60000-80a7ffff
              *-disk:0
                   description: SCSI Disk
                   product: DTN036W3UWDY10FN
                   vendor: IBM-ESXS
                   physical id: 0.0.0
                   bus info: scsi@2:0.0.0
                   logical name: /dev/sda
                   version: S25J
                   serial: [REMOVED]
                   size: 33GiB (36GB)
                   capacity: 34GiB (37GB)
                   capabilities: 10000rpm partitioned partitioned:dos
                   configuration: ansiversion=3 logicalsectorsize=512 sectorsize=512 signature=eb5eeb5e
                 *-volume
                      description: Windows NTFS volume
                      physical id: 1
                      bus info: scsi@2:0.0.0,1
                      logical name: /dev/sda1
                      version: 3.1
                      serial: [REMOVED]
                      size: 33GiB
                      capacity: 33GiB
                      capabilities: primary bootable ntfs initialized
                      configuration: clustersize=4096 created=2008-11-15 01:27:38 filesystem=ntfs state=clean
              *-disk:1
                   description: SCSI Disk
                   product: DTN036W3UWDY10FN
                   vendor: IBM-ESXS
                   physical id: 0.1.0
                   bus info: scsi@2:0.1.0
                   logical name: /dev/sdb
                   version: S25J
                   serial: [REMOVED]
                   size: 33GiB (36GB)
                   capacity: 34GiB (37GB)
                   capabilities: 10000rpm partitioned partitioned:dos
                   configuration: ansiversion=3 logicalsectorsize=512 sectorsize=512 signature=000010ab
                 *-volume:0
                      description: EXT4 volume
                      vendor: Linux
                      physical id: 1
                      bus info: scsi@2:0.1.0,1
                      logical name: /dev/sdb1
                      logical name: /
                      version: 1.0
                      serial: [REMOVED]
                      size: 32GiB
                      capacity: 32GiB
                      capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                      configuration: created=2017-11-13 22:45:42 filesystem=ext4 lastmountpoint=/ modified=2017-11-15 08:44:44 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-11-15 08:44:50 state=mounted
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: scsi@2:0.1.0,2
                      logical name: /dev/sdb2
                      size: 1458MiB
                      capacity: 1458MiB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/sdb5
                         capacity: 1458MiB
                         capabilities: nofs
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:a480(size=16) memory:20000000-200003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1000(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:6000(size=256) ioport:6400(size=64) memory:80200000-802001ff memory:80200400-802004ff
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD-ROM GDR8161B
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: 0043
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc



```

One question, I have used this old computer strictly to muddle with old MUD servers for 7 or 8 years now, but to this day, and using old Fedora, then got into Ubuntu 8ish, and now I am currently running Lubuntu 16, I have never been able to get the audio to work except in Windows. In windows Hardware Manager, it shows ¨Realtek AC97 Audio¨ for the drivers. With Lubuntu now running smoothly and stock again, any suggestions on how to tackle this? Or is this for a new post. Everything I have researched points to >  It should work Realtek AC97 was incorporated in 2005 which unfortunity dosnt solve the issue.

Thanks,

Joe.

---

### Post by mörgæs on 2017-11-15
Lubuntu 12.04 is out of support and hence a security hazard. Same goes for Windows XP. 

I recommend that you at least delete Lubuntu. XP should not be used for net access; maybe you can let this one go, too?


With only 512 MB of memory you can't expect any live boot to work. I suggest that you try the alternate Lubuntu 17.10. Please read the link in my signature for more info.

The sound problem is an issue for later when a trustworthy operative system has been installed.

---

### Post by lnewlfe on 2017-11-15
WinXP isn't used anymore, other then backup of server files when I´m dumping a Linux distro. I am not currently running 12.04, I am running 16.04 LTS. Only used a 12.04 alt disc for install. Amazingly enough all the edubuntu live boots did work, albeit not very quickly, but at least enough to redo GRUB etc.

Is 16.04 LTS trustworthy for the time being?

---

### Post by mörgæs on 2017-11-16
Yes, 16.04 is fine and will be supported through april 2019.

---

