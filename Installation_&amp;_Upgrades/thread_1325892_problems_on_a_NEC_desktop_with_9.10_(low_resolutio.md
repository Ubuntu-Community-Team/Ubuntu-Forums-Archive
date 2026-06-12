---
title: "problems on a NEC desktop with 9.10 (low resolution) and 8.04(busybox+initramfs)"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by RodGer GR on 2009-11-13
Hello there. This is my first post here.

I want to install ubuntu on a friend's pc and I have problems with hardy heron as also with karmic koala.

First of all this is the output of sudo lshw: 
```
ubuntu                    
   [B] description: Desktop Computer
    product: POWERMATE_ML460_PRO
    vendor: NEC COMPUTERS SAS[/B]
    version: PM-F-ML460-PRO
    serial: 208268560001
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=E452A619-892E-DC11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: Q965T-NP
       vendor: ELITEGROUP COMPUTER SYSTEMS CO., LTD
       physical id: 0
     *-firmware
          description: BIOS
          vendor: NEC COMPUTERS SAS NOTE BIOS Version
          physical id: 0
          version: 965Q0190 (03/28/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU            2140  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.15.2
          serial: 0000-06F2-0000-0000-0000-0000
          slot: Socket 775
          size: 1200MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
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
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 0x4D332037385436353533455A532D43453620
             vendor: 0xCE00000000000000
             physical id: 0
             serial: 0xF8102FFD
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.2
          serial: 0000-06F2-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
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
        *-pci:0
             description: PCI bridge
             product: 82Q963/Q965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:a000(size=4096) memory:fd700000-fd7fffff ioport:fd600000(size=1048576)
        *-display
             description: [B]VGA compatible controller
             product: 82Q963/Q965 Integrated Graphics Controller[/B]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:fda00000-fdafffff memory:d0000000-dfffffff(prefetchable) ioport:ff00(size=8)
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
             configuration: driver=heci latency=0
             resources: irq:16 memory:fdfff000-fdfff00f
        *-ide:0 UNCLAIMED
             description: IDE interface
             product: 82Q963/Q965 PT IDER Controller
             vendor: Intel Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi cap_list
             configuration: latency=0
             resources: ioport:fe00(size=8) ioport:fd00(size=4) ioport:fc00(size=8) ioport:fb00(size=4) ioport:fa00(size=16)
        *-network
             description: Ethernet interface
             product: 82566DM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:16:ec:92:1a:ec
             size: 100MB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.1-0 ip=192.168.178.29 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
             resources: irq:27 memory:fdfc0000-fdfdffff memory:fdffe000-fdffefff ioport:f900(size=32)
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:f800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:f700(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fdffd000-fdffd3ff
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
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:fdff4000-fdff7fff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:d000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:c000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576)
           *-storage
                description: SATA controller
                product: JMB361 AHCI/IDE
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:17 memory:fdcfe000-fdcfffff memory:fdb00000-fdb0ffff(prefetchable)
           *-ide
                description: IDE interface
                product: JMB361 AHCI/IDE
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                logical name: scsi4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0
                resources: irq:18 ioport:cf00(size=8) ioport:ce00(size=4) ioport:cd00(size=8) ioport:cc00(size=4) ioport:cb00(size=16)
              *-cdrom
                   description: DVD reader
                   product: UJDA770 DVD/CDRW
                   vendor: MATSHITA
                   physical id: 0.0.0
                   bus info: scsi@4:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/dvd
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   logical name: /cdrom
                   version: 1.02
                   capabilities: removable audio cd-r cd-rw dvd
                   configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
                 *-medium
                      physical id: 0
                      logical name: /dev/cdrom
                      logical name: /cdrom
                      configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:f600(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:f500(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:f400(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fdffc000-fdffc3ff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:b000(size=4096) memory:fd900000-fd9fffff ioport:fd800000(size=1048576)
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
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f300(size=8) ioport:f200(size=4) ioport:f100(size=8) ioport:f000(size=4) ioport:ef00(size=16) ioport:ee00(size=16)
           *-disk
                description: ATA Disk
                product: ST3160815AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 9RA1L3HM
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2aff8c51
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: a0405a69-7bcd-d948-ab9a-0a16c99de2a6
                   size: 17GiB
                   capacity: 17GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-11-11 20:27:46 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 131GiB
                   capacity: 131GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 14GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 112GiB
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 4094MiB
                      capabilities: nofs
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /media/d8d984b5-ab4b-4239-87a0-e65fe451cfbc
                   version: 1.0
                   serial: d8d984b5-ab4b-4239-87a0-e65fe451cfbc
                   size: 125MiB
                   capacity: 125MiB
                   capabilities: primary journaled extended_attributes recover ext3 ext2 initialized
                   configuration: created=2009-11-13 23:30:05 filesystem=ext3 modified=2009-11-14 01:18:55 mount.fstype=ext3 mount.options=rw,nosuid,nodev,relatime,errors=continue,data=writeback mounted=2009-11-14 01:18:55 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fdffb000-fdffb0ff ioport:500(size=32)

```(sorry if there is and some information not needed) 

First of all I installed **9.10** karmic koala and initially everything seemed ok. BUT when I tried to change the display resolution I saw that there was **no higher (than 800x600) resolution available**. I tried to search for drivers using synaptic but no succeed.

Then I tried in a live session 8.04 and there was no problem to set a higher resolution (don't remember exactly) that was ok (although lower than the resolution supported using the same system with windows xp). I rebooted to install 8.04 but again and again I got the following message:
> BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash) 
Enter ‘help’ for a list of built-in commands.

(initramfs)(or something very similar) after loading linux kernel.

I googled it a little and found as a solution using the **alternate i386 ubuntu 8.04.3**. I installed again using this CD. The installation went fine and after rebooting the first time my system worked fine.But after updating (recommended automatic updates) and rebooting again I got the same message with **BusyBox** and **initramfs** like before.

Now I really don't know what to do. Please, I need any solution that would make ubuntu 9.10 or ubuntu 8.04 work without any problem. Help my friend see the light.

Thanks in advance.

---

### Post by RodGer GR on 2009-11-14
Is there any solution to improve the resolution for Karmic Koala or any way to stop the busybox+initramfs message for Hardy Heron?

Can anybody give me a hint. Which problem seems easier? It would help me even if I had an answer on which problem I should concentrate on.

---

