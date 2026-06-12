---
title: "Daily build freezes during boot"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MadsRH on 2010-04-02
I cannot boot/install Lucid daily build friday 2. apr. How do I file a bug?

After displaying the new splash for a while, the drive just stops loading and the animation stops. 
[IMG]http://lh6.ggpht.com/_1QSDkzYY2vc/S47Fu4uYWsI/AAAAAAAAAcY/9KExu6KAKpc/s400/boot.png[/IMG]

I have no idea what is causing this, but I blame my nVidia GeForce 7300LE card and Nouveau.
How can I create a good bugreport when I cant use UbuntuBug? :confused:

```
ubuntu@ubuntu:~$ sudo lshw
ubuntu                    
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: Rev 1.xx
    serial: SYS-1234567890
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=80699EFF-B99E-DC11-BAD0-001E8C141846
  *-core
       description: Motherboard
       product: P5LD2-X/1333
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev x.xx
       serial: MT707BK05900566
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0212 (07/31/2008)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: LGA 775
          size: 1998MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 333MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: internal write-back instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 30
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1998MHz
          capacity: 1998MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:e000(size=4096) memory:ddf00000-dfffffff ioport:e0000000(size=268435456)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: G72 [GeForce 7300 LE]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:df000000-dfffffff memory:e0000000-efffffff(prefetchable) memory:de000000-deffffff memory:ddfe0000-ddffffff(prefetchable)
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:19 memory:ddcf8000-ddcfbfff
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:d000(size=4096)
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:c000(size=4096) memory:dde00000-ddefffff
           *-network
                description: Ethernet interface
                product: L2 100 Mbit Ethernet Adapter
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: a0
                serial: 00:1e:8c:14:18:46
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 duplex=full firmware=L2 ip=192.168.1.34 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:27 memory:ddec0000-ddefffff memory:ddea0000-ddebffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:8000(size=32)
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:8400(size=32)
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:8800(size=32)
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:9000(size=32)
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:ddcffc00-ddcfffff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:b000(size=4096) memory:ddd00000-dddfffff
           *-usb:0
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: 2
                bus info: pci@0000:01:02.0
                version: 50
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=uhci_hcd latency=64
                resources: irq:22 ioport:b400(size=32)
           *-usb:1
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: 2.1
                bus info: pci@0000:01:02.1
                version: 50
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=uhci_hcd latency=64
                resources: irq:23 ioport:b800(size=32)
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: VIA Technologies, Inc.
                physical id: 2.2
                bus info: pci@0000:01:02.2
                version: 51
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ehci_hcd latency=64
                resources: irq:20 memory:dddffc00-dddffcff
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:22 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-cdrom
                description: DVD writer
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                capabilities: audio cd-r cd-rw dvd dvd-r
                configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:23 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9800(size=4) ioport:9400(size=16)
           *-disk:0
                description: ATA Disk
                product: SAMSUNG HD252KJ
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: CM10
                serial: S0NJJ90Q204081
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000077fb
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: e6341612-82c9-47cd-9085-f2edf798c969
                   size: 212GiB
                   capacity: 212GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-02-26 20:43:21 filesystem=ntfs label=250GB Samsung state=clean
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 1.0
                   serial: 32742300-8e1f-4a09-9920-8aeef39c5916
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary extended partitioned partitioned:extended journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2008-10-09 21:29:48 filesystem=ext3 modified=2009-06-10 08:46:49 mounted=2009-06-10 08:40:07 state=clean
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 14GiB
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: e28ccfcb-166c-4045-9ad2-330097244564
                   size: 5938MiB
                   capacity: 5938MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-disk:1
                description: ATA Disk
                product: INTEL SSDSA2M040
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: 2CV1
                serial: CVGB005001JG040GGN
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=6cdef968
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 60c7-b3ca
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-02-26 12:46:56 filesystem=ntfs label=Reserveret til systemet state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdb2
                   version: 3.1
                   serial: a8a6d10e-79ba-074d-9eb9-8d9e17afb7fe
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-02-26 12:46:57 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi
          physical id: 2
          bus info: usb@1:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sdf

```

---

### Post by TheNerdAL on 2010-04-02
Can you still get to terminal?

And also, how did you get your splash screen like that?! I want that one! :( Mine is all messed up looking.

---

### Post by MadsRH on 2010-04-03
> **TheNerdAL said:**
> Can you still get to terminal?

No, I was never able to get to the terminal. The *lshw * above is from my Jaunty hard-drive.

> **TheNerdAL said:**
> And also, how did you get your splash screen like that?! I want that one! :( Mine is all messed up looking.

That's the new splash - it's default on the LiveCD.

If I can't blame Nouveau (*actually had everything working in the Alpha that introduced Nouveau*) I guess it must be Plymouth or ??? Any suggestions? :confused:

---

### Post by babyhuey on 2010-04-03
Removing splash from the kernel line in grub let me boot.

---

### Post by mdurham on 2010-04-04
Sorry can't resist. It says in the stickies " Sticky:    Beta 2 Freeze" would that explain it?

---

