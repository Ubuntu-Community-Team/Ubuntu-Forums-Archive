---
title: "Ubuntu 14.04 LTS hangs on Preparing to Install"
date: 2015-08-16
forum: Installation &amp; Upgrades
---

### Post by kreese2 on 2015-08-16
I'm currently trying to install Ubuntu from Live Mode via a USB stick. I set it up using Pen Drive Linux, and have Windows 7 installed alongside it. My specs are as follows:

```
2GB RAM
500GB HDD
Intel HD Graphics (on-board)
```

I've been spending hours looking up how to install this, looking for solutions, and experimenting with it myself.

Here is the output of sudo-lshw:
```
    description: Desktop Computer
    product: SX2855 (To be filled by O.E.M.)
    vendor: Gateway
    version: P01-B2
    serial: DTGCFAA002209036889600
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=Gateway Desktop power-on_password=disabled sku=To be filled by O.E.M. uuid=8EC68817-2D9E-4F34-8794-BCC9F629B2CD
  *-core
       description: Motherboard
       product: SX2855
       vendor: Gateway
       physical id: 0
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P01-B2
          date: 08/16/2011
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU G460 @ 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Celeron(R) CPU G460 @ 1.80GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1599MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer xsave lahf_lm arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid xsaveopt cpufreq
          configuration: cores=1 enabledcores=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 1536KiB
             capacity: 1536KiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM [empty]
             vendor: Manufacturer1
             physical id: 0
             serial: SerNum1
             slot: DIMM1
             width: 64 bits
        *-bank:1
             description: DIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: ACR256X64D3U13C9G
             vendor: Kingston
             physical id: 1
             serial: 4912E1C5
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=snb_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:27 memory:fe000000-fe3fffff memory:d0000000-dfffffff ioport:f000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:28 memory:fe429000-fe42900f
        *-network
             description: Ethernet interface
             product: 82579V Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 05
             serial: c8:9c:dc:a6:ce:6f
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.13-4 ip=192.168.0.3 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:25 memory:fe400000-fe41ffff memory:fe428000-fe428fff ioport:f080(size=32)
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:fe427000-fe4273ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:29 memory:fe420000-fe423fff
        *-pci
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fe426000-fe4263ff
        *-isa
             description: ISA bridge
             product: H61 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:26 ioport:f0d0(size=8) ioport:f0c0(size=4) ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f060(size=32) memory:fe425000-fe4257ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe424000-fe4240ff ioport:f040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD A  DH16ABSH
             vendor: ATAPI
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: YA12
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HDS72105
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: A50E
             serial: JP1570FN26D90K
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=b753943f
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: fef3-ea9b
                size: 19GiB
                capacity: 20GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2013-01-09 23:06:17 filesystem=ntfs label=PQSERVICE state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: d076-016f
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-01-10 00:07:20 filesystem=ntfs label=SYSTEM RESERVED state=clean
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: 3699729b-1255-5641-ab3e-f29cba304ff7
                size: 367GiB
                capacity: 367GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2013-01-10 00:07:22 filesystem=ntfs label=Gateway modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@1:0.0.0,4
                logical name: /dev/sda4
                version: 1.0
                serial: ff800ebb-df43-432f-a507-87c91701154d
                size: 78GiB
                capacity: 78GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-08-16 05:31:31 filesystem=ext4 label=UBUNTU modified=2015-08-16 05:31:32 state=clean
     *-scsi:2
          physical id: 3
          bus info: usb@1:1.1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             size: 7633MiB (8004MB)
             capabilities: partitioned partitioned:dos
             configuration: sectorsize=512
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /cdrom
                version: FAT32
                serial: 1d06-0c60
                size: 7630MiB
                capacity: 7632MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
     *-scsi:3
          physical id: 5
          bus info: usb@2:1.3
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GP08NU6B
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sr1
             logical name: /media/ubuntu/CDROM
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/sr1
                logical name: /media/ubuntu/CDROM
                capabilities: partitioned partitioned:dos
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500 signature=622d5fd6 state=mounted
              *-volume UNCLAIMED
                   description: Windows FAT volume
                   vendor: mkfs.fat
                   physical id: 2
                   version: FAT12
                   serial: aa25-20cb
                   size: 15EiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=Firmware
     *-scsi:4
          physical id: 6
          bus info: usb@1:1.3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdd
             configuration: sectorsize=512
     *-scsi:5
          physical id: 7
          bus info: usb@2:1.4
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: My Passport 0730
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sde
             version: 1008
             serial: WX91C80D5932
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=6 sectorsize=512 signature=88d6d02b
           *-volume
                description: Windows FAT volume
                vendor: BSD  4.4
                physical id: 1
                bus info: scsi@7:0.0.0,1
                logical name: /dev/sde1
                version: FAT32
                serial: 6422-1de2
                size: 931GiB
                capacity: 931GiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=AFTASHOK1
        *-enclosure UNCLAIMED
             description: SCSI Enclosure
             product: SES Device
             vendor: WD
             physical id: 0.0.1
             bus info: scsi@7:0.0.1
             version: 1008
             serial: WX91C80D5932
             configuration: ansiversion=6
```

---

### Post by dino99 on 2015-08-16
ubuntu & windows have to be set the same way, related to efi/gpt config (search 'oldfred' posts/threads about 'ubuntu alongside windows')

---

### Post by grahammechanical on 2015-08-16
So, what is the problem? You really do not say. Does the Live session run good? Do you want a guide to installing?

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

That is what you will see if you select the Install alongside option. If you choose the Something Else option then you will see dialogs like these and have to make to correct decisions.

[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

