---
title: "my new pc 10.04 works great ... 12.04 GUI breaks"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by Dodeca on 2013-02-19
Hello all ...

My "new" pc is a dell precision T4300.

I have made it into a dual boot 10.04 and 12.04 ( currently running on 10.04)

And 10.04 works perfect !!! 

12.04 ( fresh install and no errors ) will boot past grub and my login ... but then all the icon launchers on the left are missing ... just an orange strip top to bottom and when you move the mouse over the area ... they are THERE !

So I can launch apps but it seems the GUI crashes and start giving me error text messages 

here is the results of lshw

```

xxx-desktop               
    description: Tower Computer
    product: Precision WorkStation T3400
    vendor: Dell Inc.
    serial: 8G2LCF1
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: administrator_password=enabled boot=normal chassis=tower power-on_password=enabled uuid=44454C4C-4700-1032-804C-B8C04F434631
  *-core
       description: Motherboard
       product: 0TP412
       vendor: Dell Inc.
       physical id: 0
       serial: ..CN708217BF504L.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A09 (06/04/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: CPU
          size: 2333MHz
          width: 64 bits
          clock: 1333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 4MiB
             capacity: 4MiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: NT1GT64U8HB0BY-3C
             vendor: 7F7F7F0B00000000
             physical id: 0
             serial: 377A1B45
             slot: DIMM_1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: HYMP512U64CP8-Y5
             vendor: AD00000000000000
             physical id: 1
             serial: 04004057
             slot: DIMM_3
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: NT1GT64U8HB0BY-3C
             vendor: 7F7F7F0B00000000
             physical id: 2
             serial: 137A1B41
             slot: DIMM_2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: KCM633-ELC
             vendor: 7F98000000000000
             physical id: 3
             serial: 9E2E4FCE
             slot: DIMM_4
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: 82X38/X48 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=x38_edac
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 82X38/X48 Express Host-Primary PCI Express Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 memory:fb000000-fdefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: NV38GL [Quadro FX 1300]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fb000000-fbffffff memory:d0000000-dfffffff(prefetchable) memory:fc000000-fcffffff memory:fde00000-fde1ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 82X38/X48 Express Host-Secondary PCI Express Bridge
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff20(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:ff00(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:ecc0(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:fdffbc00-fdffbfff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fdffc000-fdffffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:1000(size=4096) memory:faf00000-faffffff memory:f0000000-f01fffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:2000(size=4096) memory:fae00000-faefffff memory:f0200000-f03fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 02
                serial: 00:1d:09:23:bf:8a
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5754-v3.24 ip=192.168.1.102 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:29 memory:faef0000-faefffff
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff80(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:ff60(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ff980800-ff980bff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:28 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fec0(size=32) memory:ff970000-ff9707ff
           *-disk
                description: ATA Disk
                product: Hitachi HDS72101
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: GKAO
                serial: GTE000PAGE515E
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0001cd4e
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: ac2352b7-7686-4d22-8585-6dad4e3b8165
                   size: 471GiB
                   capacity: 471GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2013-02-19 16:48:50 filesystem=ext4 lastmountpoint=/nt/migrationassistant8]&#65533;&#65533;&#65533;&#65533;&#65533;L#&#65533;c(]&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533;&#65533;@&#65533;O&#968;&#65533;&#65533; modified=2013-02-19 17:24:38 mounted=2013-02-19 19:33:18 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 460GiB
                   capacity: 460GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4028MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 445GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 11GiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD-RW  DVR-215D
                vendor: PIONEER
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.13
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fdffbb00-fdffbbff ioport:ece0(size=32)
     *-scsi
          physical id: 1
          bus info: usb@1:3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             size: 7633MiB (8004MB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/D012-91C4
                version: FAT32
                serial: d012-91c4
                size: 7633MiB
                capacity: 7633MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted


```

thanks

---

### Post by kagashe on 2013-02-19
Hi,

Ubuntu 12.04 has two versions now with different Kernels and Xorg.

If you have downloaded recently it would be Ubuntu 12.04.2 and if it is original it would be 12.04.

If it is Ubuntu 12.04 or 12.04.1 you can try 12.04.2 and vice versa.

Kamalakar

---

### Post by Dodeca on 2013-02-21
I have solved the problem by installing LINUX MINT.

Thanks 4 trying.

Dodeca

---

