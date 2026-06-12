---
title: "Boot problem after fresh install of Lubuntu 13.10"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by rdh61 on 2013-10-20
Hi,

I have freshly installed Lubuntu 13.10 on an old Advent laptop (1000 MB RAM) which was previously running Ubuntu 12.04. I changed because I felt Unity was a bit heavy for this machine and was quite slow. The installation appeared to have carried through successfully (in fact it told me it had).

However, the new installation does not boot successfully. After the splash screen I get an endlessly repeating black screen with the following:

* Starting LightDM Display Manager  (OK)

* Stopping Send an event to indicate plymouth is up  (OK)

Any suggestions gratefully received.

Many thanks.

---

### Post by mörgæs on 2013-10-20
Please run

```
sudo lshw -sanitize > lshw.txt

```
and post lshw.txt in CODE tags.

---

### Post by rdh61 on 2013-10-21
> **mörgæs said:**
> Please run

```
sudo lshw -sanitize > lshw.txt

```
and post lshw.txt in CODE tags.

Thanks for your answer. Please could you tell me how to do that, since my OS won't load? Do I use the live CD? If so, is it simply a question of opening a terminal and typing the above code?

Sorry about the idiot questions, but I've learned that what must seem obvious to the technically savvy often isn't so straightforward to me!

---

### Post by mörgæs on 2013-10-21
> **rdh61 said:**
> Do I use the live CD? If so, is it simply a question of opening a terminal and typing the above code?

Yes and yes.

---

### Post by rdh61 on 2013-10-22
Here is lshw.txt:

```
computer
    description: Desktop Computer
    version: 1.0
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: To be filled by O.E.M.
       vendor: To be filled by O.E.M.
       physical id: 0
       version: 1.0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080011
          date: 02/07/2006
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: CPU 1
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 1GiB
          capacity: 3GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
     *-pci
          description: Host bridge
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:dfe00000-dfefffff memory:cfd00000-dfcfffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller cap_list
                configuration: latency=0
                resources: memory:d0000000-d7ffffff memory:dfee0000-dfefffff ioport:cc00(size=128)
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO] LPC Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2/3 SMBus controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:c00(size=32)
        *-ide
             description: IDE interface
             product: 5513 IDE Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-disk
                description: ATA Disk
                product: HTS424040M9AT00
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MA2O
                serial: [REMOVED]
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=41c40640
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: [REMOVED]
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-09-18 15:02:54 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 23GiB
                   capacity: 23GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1913MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 21GiB
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7560A
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                logical name: /cdrom
                version: DX06
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   capabilities: partitioned partitioned:dos
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=524909a3 state=mounted
                 *-volume UNCLAIMED
                      description: Hidden HPFS/NTFS partition
                      physical id: 1
                      capacity: 688MiB
                      capabilities: primary bootable hidden
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=64 maxlatency=11 mingnt=52
             resources: ioport:e400(size=256) ioport:e000(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: SiS7012 AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=64 maxlatency=11 mingnt=52
             resources: irq:18 ioport:e800(size=256) ioport:ec00(size=128)
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:dfffd000-dfffdfff
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:dfffe000-dfffefff
        *-usb:2
             description: USB controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: irq:23 memory:dffff000-dfffffff
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: [REMOVED]
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=64 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10Mbit/s
             resources: irq:19 ioport:d800(size=256) memory:dfffc000-dfffcfff memory:dffc0000-dffdffff
     *-scsi
          physical id: 1
          bus info: usb@1:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: Windows FAT volume
             vendor: mkdosfs
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             logical name: /media/ADATA
             version: FAT32
             serial: [REMOVED]
             size: 7508MiB
             capacity: 7509MiB
             capabilities: fat initialized
             configuration: FATs=2 filesystem=fat label=ADATA mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted



```

Thanks.

---

### Post by mörgæs on 2013-10-23
It seems we have another problem with SIS graphics. 

If you want to use Lubuntu, which is a good choice for a somewhat weak computer, there are workarounds but I have never tried installing myself.

Second-best option is to try Xubuntu 12.04.

---

### Post by rdh61 on 2013-10-23
Hi, I've gone back to the 12.04 version of Lubuntu, which works fine. Thanks for your help.

---

### Post by mörgæs on 2013-10-23
12.04 of Lubuntu is unsupported and hence a security risk. Xubuntu 12.04 is supported through april 2015.

---

### Post by rdh61 on 2013-11-05
> **mörgæs said:**
> 12.04 of Lubuntu is unsupported and hence a security risk. Xubuntu 12.04 is supported through april 2015.

Hmmm... distressing that Lubuntu support is so short-lived. Have taken your advice and installed Xubuntu 12.04. Thank you.

---

### Post by mörgæs on 2013-11-05
You are welcome. 

Lubuntu is maintained by a few volunteers. Until now there has simply not been enough hands for keeping a long term support release running, but it might change with 14.04.

---

