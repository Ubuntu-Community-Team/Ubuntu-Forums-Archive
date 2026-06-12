---
title: "Bad image quality"
date: 2016-01-24
forum: Installation &amp; Upgrades
---

### Post by Hankbonk on 2016-01-24
i have installed Lubuntu 15.10, and I get blur images in my dialog boxes !  What can I do ?

---

### Post by oldos2er on 2016-01-24
Provide some more information; hardware specs, particularly video card and drivers (if known). Does the problem only occur in dialog boxes? Perhaps let us see a screenshot.

---

### Post by Hankbonk on 2016-01-25
oldos2er,

I don't see what difference that would make,since I have the same configuration on Lubuntu 14.04 LTS and there (here) I do not have the problem !
The blur images are everywhere : In dialog boxes, everywhere that I try to type in information or choose from a menu list .

I have loaded Lubuntu 15.10 with Netbootin on a USB stick, and installed it from that stick .

Regards, Hankbonk .

---

### Post by vasa1 on 2016-01-25
> **Hankbonk said:**
> oldos2er,

I don't see what difference that would make,since I have the same configuration on Lubuntu 14.04 LTS and there (here) I do not have the problem !
The blur images are everywhere : In dialog boxes, everywhere that I try to type in information or choose from a menu list .

I have loaded Lubuntu 15.10 with Netbootin on a USB stick, and installed it from that stick .

Regards, Hankbonk .

What's your difficulty in providing the information requested? Things aren't necessarily the same in 14.04 and 15.10. For example, the kernels are different. Newer kernels may not play nice with older hardware.

---

### Post by Hankbonk on 2016-01-25
ok, then tell me how to get that info oldos2er requested please, vasa1

this is my info

```
 *-display               
       description: VGA compatible controller
       product: 82Q963/Q965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f0400000-f04fffff memory:e0000000-efffffff ioport:1100(size=8)
```

more 
```
henk-hp-compaq-dc7700-small-form-factor
    description: Low Profile Desktop Computer
    product: HP Compaq dc7700 Small Form Factor (RG576AW#AK6)
    vendor: Hewlett-Packard
    serial: CZC7220P04
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=low-profile cpus=2 family=103C_53307F sku=RG576AW#AK6 uuid=98C53C09-6C0E-DC11-BBDA-784A9654001B
  *-core
       description: Motherboard
       product: 0A54h
       vendor: Hewlett-Packard
       physical id: 0
       serial: CZC7220P04
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 1
          version: 786E1 v01.10
          date: 04/13/2007
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.40GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.6.5
          serial: 0000-0F65-0000-0000-0000-0000
          slot: XU1 PROCESSOR
          size: 2400MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 800MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm cpufreq
          configuration: cores=2 enabledcores=2 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 7
             slot: L1 Cache
             size: 28KiB
             capacity: 28KiB
             capabilities: burst internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 8
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-cpu:1 DISABLED
          description: CPU [empty]
          vendor: Intel
          physical id: 6
          slot: XU2 PROCESSOR
     *-memory:0
          description: System Memory
          physical id: 37
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1,5 ns)
             product: M3 78T6553EZS-CE6
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 0
             serial: 0DC305F8
             slot: XMM1
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1,5 ns)
             product: M3 78T6553EZS-CE6
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 1
             serial: 45CF18F9
             slot: XMM2
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1,5 ns)
             product: M3 78T6553EZS-CE6
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 2
             serial: 05C305F8
             slot: XMM3
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous [empty]
             vendor: JEDEC ID:
             physical id: 3
             slot: XMM4
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 38
          slot: System board or motherboard
          capacity: 1MiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 1MiB
             width: 2 bits
     *-cpu:2
          physical id: 0
          bus info: cpu@1
          version: 15.6.5
          serial: 0000-0F65-0000-0000-0000-0000
          size: 2400MHz
          capacity: 2400MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-memory:2 UNCLAIMED
          physical id: 2
     *-memory:3 UNCLAIMED
          physical id: 3
     *-pci
          description: Host bridge
          product: 82Q963/Q965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82Q963/Q965 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:f0400000-f04fffff memory:e0000000-efffffff ioport:1100(size=8)
        *-communication
             description: Communication controller
             product: 82Q963/Q965 HECI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:42 memory:f0525900-f052590f
        *-network
             description: Ethernet interface
             product: 82566DM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:1b:78:4a:96:54
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=1.1-0 ip=192.168.0.164 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:41 memory:f0500000-f051ffff memory:f0524000-f0524fff ioport:1000(size=32)
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1020(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1040(size=32)
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:22 memory:f0525000-f05253ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f0520000-f0523fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:60000000-601fffff ioport:60200000(size=2097152)
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1060(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1080(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:f0525400-f05257ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801HO (ICH8DO) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:10e0(size=16) ioport:10f0(size=16)
     *-scsi:0
          physical id: 4
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST380815AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.CH
             serial: 5RW0BRKK
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000ca8af
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 5d2facc4-77dd-4de6-a0ca-f354340318d3
                size: 49GiB
                capacity: 49GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-03-10 03:21:35 filesystem=ext4 lastmountpoint=/ modified=2016-01-24 11:41:37 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-01-24 11:41:37 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 24GiB
                capacity: 24GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1518MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 23GiB
     *-scsi:1
          physical id: 7
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD-ROM GDRH10N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: D70D
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc
```

---

### Post by kansasnoob on 2016-01-25
Blurred as bad as this image?:

[https://launchpadlibrarian.net/221590308/IMG_5038.JPG](https://launchpadlibrarian.net/221590308/IMG_5038.JPG)

If so it's this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507255](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507255)

I'm personally just sticking with 14.04 (Trusty) in hopes we can get that sorted out by the time it reaches EOL - April 2017 in the case of Lubuntu. But others have tried a workaround as shown in comment #5 of that bug report with some success.

---

### Post by Hankbonk on 2016-01-25
Thanks kansasnoob, that's it !

I will stay in 14.04 LTS, untill the new version is out of bugs or there is a fix for that bug !!!

I will close this thread now .

---

