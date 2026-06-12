---
title: "Viglen &quot;LCD PC&quot;, graphics garbled on boot"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by RoboJ1M on 2011-11-14
Hi,

I've been given a Viglen "LCD PC" to try to turn it into a cheap web browsing machine running Ubuntu.

Left to it's own devices you get a screen full of garbage, the screen's being driven at a wrong resolution by the looks of it.

Adding ```
nomodeset
``` as a kernel param boots fine, you get 1024x768 24bit fine, using the software video driver.

I tried adding vga=792 (1024x768x24) as a kernel param and you just get a black screen, or more garbled, can't remember which right now.

```
hwinfo --framebuffer
``` lists mode 792 as supported.

Can anybody help sort this out?

Thanks,

James.

Hardware Spec:

CPU: Celeron 2.40GHz
RAM: 256Mb RAM shared with GPU
Chipset: Intel 865G 
Monitor: 15" XGA LCD Panel (supporting a resolution of 1024*768 256K colors)

(I can dump ldhw if it's of any use)

---

### Post by RoboJ1M on 2011-11-18
Hi,

OK, still bashing away at the problem.
I tried various things from the sticky thread in this section, the only thing that made any difference is editing the grub defaults file and setting the mode to 1024x768.

The only thing that does is give me a high resolution screen IN the grub menu

Handy, but doesn't fix the problem.

The following kernel params do nothing:

vga=xxx
xforcevesa

I've attached a screen shot fwiw, it looks like the screens being driven out of range.

Ubuntu has booted and sits at gdm, you can sometimes tap the power button and it will shut down.

ctrl+alt+f1 will switch to terminal, but still garbled.

the kernel param nomodeset will work, 1024x768x24 with a software rasteriser.

I've tried updating the OS and there are no binary drivers to install.
I'll post lshw next from the machine itself.

---

### Post by RoboJ1M on 2011-11-18
OK, here's the complete lshw for the machine:

```
l295p-01
    description: Computer
    version: N/A
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=0090F516-BACD-0000-0000-000000000000
  *-core
       description: Motherboard
       product: L297P
       vendor: CLEVO Co.
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 3.01P/U
          date: 07/15/2004
          size: 113KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: WMT478/NWD
          size: 2400MHz
          capacity: 3GHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 8KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 128KiB
             capacity: 512KiB
             capabilities: burst internal write-back
     *-cache
          description: L3 cache
          physical id: 7
          slot: L3 Cache
          size: 128KiB
          capacity: 512KiB
          capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 256MiB
        *-bank:0
             description: DIMM DDR Synchronous 133 MHz (7.5 ns)
             physical id: 0
             slot: J6G1
             size: 256MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 133 MHz (7.5 ns) [empty]
             physical id: 1
             slot: J6G2
             clock: 133MHz (7.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 133 MHz (7.5 ns) [empty]
             physical id: 2
             slot: J6H1
             clock: 133MHz (7.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 133 MHz (7.5 ns) [empty]
             physical id: 3
             slot: J6H2
             clock: 133MHz (7.5ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:0-7ffffff
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:e8000000-e807ffff ioport:2070(size=8)
        *-generic UNCLAIMED
             description: Unassigned class
             product: Illegal Vendor ID
             vendor: Illegal Vendor ID
             physical id: 6
             bus info: pci@0000:00:06.0
             version: ff
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master vga_palette cap_list
             configuration: latency=255 maxlatency=255 mingnt=255
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1cc0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1ce0(size=32)
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:2000(size=32)
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:2020(size=32)
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:e8080000-e80803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:e8100000-e81fffff memory:10000000-17ffffff
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 6
                bus info: pci@0000:03:06.0
                logical name: eth0
                version: 10
                serial: 00:90:f5:16:ba:cd
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.88.16 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:18 ioport:3000(size=256) memory:e8100000-e81000ff
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 7
                bus info: pci@0000:03:07.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:e8101000-e8101fff ioport:3400(size=256) ioport:3800(size=256) memory:10000000-13ffffff memory:1c000000-1fffffff
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 7.1
                bus info: pci@0000:03:07.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:17 memory:e8102000-e8102fff ioport:3c00(size=256) ioport:2400(size=256) memory:14000000-17ffffff memory:20000000-23ffffff
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:2060(size=16) memory:18000000-180003ff
           *-disk
                description: ATA Disk
                product: ST3802110A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 9LS4E8ME
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000896fc
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 498718a1-0211-4a80-bbc1-5d83383f1e9b
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-11-12 16:18:09 filesystem=ext4 lastmountpoint=/ modified=2011-11-12 18:26:38 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-11-18 18:06:24 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: cd0e171c-a19c-4d4d-8222-7a26ce938650
                   size: 2931MiB
                   capacity: 2931MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-C2612
                vendor: TOSHIBA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1J11
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:2040(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:1400(size=256) ioport:1c80(size=64) memory:e8080c00-e8080dff memory:e8080800-e80808ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:1800(size=256) ioport:1c00(size=128)
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound
```

---

