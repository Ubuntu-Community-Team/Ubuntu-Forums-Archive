---
title: "No GUI when attempting boot from [usb]LiveCD"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by mcklucker on 2012-12-01
I am attempting to install Ubuntu 12.04 on this HP Mini, and hitting snag after snag.  I currently have a dualboot of M$ 7 Starter and Ubuntu 10.04.  I attempted to update from 10.04 to 12.04 via the Update Manager, but I *believe* the power cable came disconnected during the update process, and now I can't install anything on the Ubuntu side.  Attempting to run Update Manager gives me this window: 
```
Not all updates can be installed
Run a partial upgrade, to install as many updates as possible.
This can be caused by:
*A previous upgrade which didn't complete
*Problems with some of the installed software
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-release version of Ubuntu
/Partial Upgrade/ /Close/
```
Partial crashes out every time I try it.  So I tried the LiveCD route with a USB drive (this netbook has no disc drives).  Attempting to boot from it gets me just a black screen with a tiny grey rectangle in the bottom left corner.  The ESC key from this screen leads me to a centered Win3.1-esque dialog window with no text, and two unmarked buttons.  I have no idea what these buttons do, so I attempted to tab to neither.  

Oh, here's my lshw if that helps.
```
makkaros@makkaros-laptop:~$ sudo lshw
[sudo] password for makkaros: 
makkaros-laptop           
    description: Notebook
    product: HP Mini 110-1100
    vendor: Hewlett-Packard
    version: 0393110000201B00000300000
    serial: CNU938773J
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=1 uuid=9924DBFA-89F0-CB8A-43EC-A2BF049162B5
  *-core
       description: Motherboard
       product: 308F
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 02.10
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 308F0 Ver. F.17 (09/16/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU 1
          size: 1600MHz
          capacity: 1666MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm pse cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 24KiB
             capacity: 24KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 1GiB
        *-bank
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
     *-generic UNCLAIMED
          physical id: 256
          bus info: parisc@256
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:fe980000-fe9fffff ioport:dc80(size=8) memory:d0000000-dfffffff(prefetchable) memory:fe940000-fe97ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fe880000-fe8fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fe938000-fe93bfff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:1000(size=4096) memory:fea00000-feafffff memory:40000000-401fffff(prefetchable)
           *-network
                description: Network controller
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:16 memory:feafc000-feafffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:e000(size=4096) memory:feb00000-febfffff memory:40200000-403fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: c0
                serial: 00:26:55:c9:11:5a
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:27 memory:febc0000-febfffff ioport:ec80(size=128)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:dc00(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d880(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d800(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d480(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fe937c00-fe937fff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
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
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:26 ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=8) ioport:cc80(size=4) ioport:cc00(size=16) memory:fe937800-fe937bff
           *-disk
                description: ATA Disk
                product: FUJITSU MJA2160B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8919
                serial: K94NT982DPD9
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cd68444d
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: caeea319-f1d1-6144-be92-a784815bd948
                   size: 100GiB
                   capacity: 100GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-08-28 14:02:32 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: f6f3f450-1e93-be49-93df-910ed8212fc8
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-09-23 21:50:11 filesystem=ntfs label=RECOVERY state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: e2e8-0c8d
                   size: 192MiB
                   capacity: 201MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-09-23 22:27:12 filesystem=ntfs label=SYSTEM state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 35GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1611MiB
                      capabilities: nofs
     *-scsi:0
          physical id: 1
          bus info: usb@1:2
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdb
     *-scsi:1
          physical id: 2
          bus info: usb@1:7
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: SanDisk Cruzer
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdc
             version: 8.02
             serial: u
             size: 3835MiB (4022MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
                size: 3835MiB (4022MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=000cb1cd
              *-volume
                   description: Windows FAT volume
                   vendor: mkdosfs
                   physical id: 1
                   logical name: /dev/sdc1
                   logical name: /media/E586-5548
                   version: FAT32
                   serial: e586-5548
                   size: 3832MiB
                   capacity: 3832MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted
  *-battery
       description: Nickel Cadmium Battery
       product: Nikon Ultra Plus
       vendor: Nikon Battery
       physical id: 1
       version: 08/11/97
       serial: NI00123
       slot: Front side of System
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 0c:60:76:1f:a2:f1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.18 multicast=yes wireless=IEEE 802.11bg
makkaros@makkaros-laptop:~$ ^C
makkaros@makkaros-laptop:~$ 

```

---

### Post by zvacet on 2012-12-02
If you didn´t install all updates try with

```
sudo apt-get update && sudo apt-get upgrade
```

If you don´t get any result with it then

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by ivotkl on 2012-12-04
I also have an Intel graphics card on my notebook. Have you tried pressing F6 key and choosing "nomodeset"?
For further information, read [this post](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1).

You can also edit and add VGA=nomodeset (or something like that, long time since I' ve used that command), but results are the same as following steps above.

Once you make a complete install, if you get the same thing, edit commands (hit E key) before choosing your Ubuntu 12.04 OS on Grub boot loader. You should add nomodeset on the line before the last one, if I recall well. According to [this guy' s post](http://ubuntuforums.org/showpost.php?p=12157390&postcount=2), it should be added right after quiet splash line. After you do that, just press CTRL+X to execute modified command.

Final step (go to terminal):
```
sudo gedit /boot/grub/grub.cfg
```
And add nomodeset on that exact same line, save, exit and restart to check it worked. On next reboot, skip steps on above paragraph.

PS: Are you going through any other situation? Because if not, this SHOULD fix it.

---

