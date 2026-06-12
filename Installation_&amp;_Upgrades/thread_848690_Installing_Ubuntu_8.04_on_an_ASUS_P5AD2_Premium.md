---
title: "Installing Ubuntu 8.04 on an ASUS P5AD2 Premium"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by hairshirt on 2008-07-03
Hi All,

Just inherited a machine I built for a chap a few years ago.  Just built him a new machine (quad core with all the gizmos).  He gave me the &#8220;old&#8221; machine as payment ... which I gladly accepted.

He uses/used windoze on both machines.

I'm having problems with the inherited machine upon which I have had no problems installing a fresh ExP  Didn't even need to press F6 to install Raid software as I configured the ITE8212F/ICH6R RAID controller as IDE.

Firstly, I would like to say that I have very few problems like the one I face here.  I have just built an Ubuntu 8.04 machine for myself that I use as a media centre (mythtv).  Based on an ASUS MSN-SLI Deluxe board.  All (cd drives also) drives being SATA.

Back to the problem I'm having.  The inherited machine is based on an ASUS P5AD2 Premium.

I wanted to build a dual boot machine ExP and Ubuntu 8.04.

I've fitted 3 x SATA Drives and also wish to install an IDE on a temporary basis to copy over files from my home directory from what was my main work machine.

2 IDE CD Drive.

2 Gig RAM

P4 3.4 Mhz

I'm having serious problems getting all this configured.  Can't get the other two SATA drive recognised in either ExP or Gparted on Ubuntu Live CD.  Added to these problems, every time I attempt an install of 8.04, I get the follow error message:  &#8220;The installer encounted an error copying files to the hard drive [Errno 5] Input/output error&#8221;.  I've tried just about every combination BIOS. Silicon Image SATA/RAID on and off and with hard drives plugged into those and ITE8212F on and off with the SATA boot drive either plugged into ITE8212F and the two other SATA drives plugged into the Silicon Image &#8211; or the main SATA boot drive plugged into SATA_RAID1 and the other two SATA Data Drive plugged into SATA 3 and 4.

Any input would be gratefully received.

---

### Post by Pumalite on 2008-07-03
Have you tried editing the boot line and adding: all_generic_ide at the end?

---

### Post by hairshirt on 2008-07-04
> **Pumalite said:**
> Have you tried editing the boot line and adding: all_generic_ide at the end?

? where??  how??

---

### Post by Pumalite on 2008-07-04
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by hairshirt on 2008-07-04
> **Pumalite said:**
> [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

Thank you ... I'll have a look

---

### Post by hairshirt on 2008-07-04
don't I have to have Ubuntu installed before this can be done?


Got It ... OK, I'll give that a go.  I'll read the whole page next time... :)

---

### Post by overdrank on 2008-07-04
> **hairshirt said:**
> don't I have to have Ubuntu installed before this can be done?

HI and no you can use the option F6 I believe and edit the kernel line. Like remove quiet splash and add noapic before the --
Edit to slow lol :)

---

### Post by hairshirt on 2008-07-04
Ok chaps,

Did that and this is what I got:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12)
Built-in shell (ash)

Enter "help" for a list of built-in commands (initramfs) [131.525019] ata 1.00:excepton
Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen blaa blaa blaa

And a whole load of other blurb

Any ideas.

Ta very much...

---

### Post by hairshirt on 2008-07-04
I wait with baited breath...

---

### Post by overdrank on 2008-07-04
> **hairshirt said:**
> I wait with baited breath...

Ok I just read your first post and are you trying to setup a raid system? You mention a raid setup with IDE and then state you are using sata drives? What option did you try to the kernel line?

---

### Post by Pumalite on 2008-07-04
Try these:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317 vga=788 vga=789 vga=791
One st the time or in different combinations.

---

### Post by hairshirt on 2008-07-04
Hi, and thanks for geting back to me.

I'm not really attempting a raid installation.  I just want all 3hd's to work.  They are sata drives but I also have a standard (old) IDE drive with a linux installation on it.  I want to copy over my home dir from that drive to the new installation.

The first attempt at an installation was to a raid setup, howerver, albeit ExP installed ok with the SATA Raid drivers on a floppy ... I just could not get Ubuntu 8.04 installed ... just kept getting the errors I mentioned in my earlier post.

Any ideas.

PS. This P5AD2 Premium board does seem to be overly complicated.

PPS. I also have to say that I can't get OpenSUSE or Mint 5 installed either.  Thought I'd try these as I couln't get Ubuntu 8.04 installed ... got the self same error message - Errno 5 input/output error

---

### Post by hairshirt on 2008-07-04
> **Pumalite said:**
> Try these:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317 vga=788 vga=789 vga=791
One st the time or in different combinations.


I'll give that simple suggestion a go :)

---

### Post by hairshirt on 2008-07-04
> **Pumalite said:**
> Try these:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317 vga=788 vga=789 vga=791
One st the time or in different combinations.

OK tried that ... all of them and in that order ... same problem.

I can't understand how windiz installed without a hitch (as much as I hate admitting it).

---

### Post by Pumalite on 2008-07-04
Post:
sudo lshw

---

### Post by hairshirt on 2008-07-04
> **Pumalite said:**
> Post:
sudo lshw

Hi and thanks for your help with this.  The file is rather long so I've attached it.

Cna't upload in linux format for some reason ... here it is a windiz txt format... sorry about that.

******** ... file too large ... here we go

    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.1 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=40DC1CA9-8DFE-D511-831F-0011D82447A2
  *-core
       description: Motherboard
       product: P5AD2-Premium
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1010.009 (02/03/2005)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: Socket 775
          size: 3400MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid xtpr
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 43
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 512MiB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 512MiB
             width: 64 bits
        *-bank:3
             description: DIMM SDRAM Synchronous
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82925X/XE Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82925X/XE PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV380 [Radeon X600 (PCIE)]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list
                configuration: latency=0
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV380 [Radeon X600]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8053 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 15
                serial: 00:11:d8:24:47:a2
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
        *-pci:3
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8053 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 15
                serial: 00:11:d8:24:4b:89
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network UNCLAIMED
                description: Ethernet controller
                product: 88W8310 and 88W8000G [Libertas] 802.11g client chipset
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 07
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB82AA2 IEEE-1394b Link Layer Controller
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:01:03.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=3 module=ohci1394
           *-storage:0
                description: Mass storage controller
                product: IT/ITE8212 Dual channel ATA RAID controller
                vendor: Integrated Technology Express, Inc.
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 13
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=pata_it821x latency=64 maxlatency=8 mingnt=8 module=pata_it821x
           *-storage:1
                description: Mass storage controller
                product: SiI 3114 [SATALink/SATARaid] Serial ATA Controller
                vendor: Silicon Image, Inc.
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=sata_sil latency=64 module=sata_sil
           *-usb:0
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: a
                bus info: pci@0000:01:0a.0
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1 module=ohci_hcd
           *-usb:1
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: a.1
                bus info: pci@0000:01:0a.1
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1 module=ohci_hcd
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: a.2
                bus info: pci@0000:01:0a.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ehci bus_master cap_list
                configuration: driver=ehci_hcd latency=64 maxlatency=34 mingnt=16 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi12
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM DVD-122
                vendor: PIONEER
                physical id: 0.0.0
                bus info: scsi@12:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: 1.00
                capabilities: removable audio dvd
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
           *-cdrom:1
                description: DVD writer
                product: DVD-RW  DVR-108
                vendor: PIONEER
                physical id: 0.1.0
                bus info: scsi@12:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.14
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: 82801FR/FRW (ICH6R/ICH6RW) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi8
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: HDS722516VLSA80
                physical id: 0.0.0
                bus info: scsi@8:0.0.0
                logical name: /dev/sda
                version: V34O
                serial: VN6D3ECDDYZ4MD
                size: 153GiB (164GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000be621
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@8:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 22e0f371-8e8a-ca44-bfce-37a1cd47343a
                   size: 153GiB
                   capacity: 153GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-07-02 17:09:07 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-scsi:0
          physical id: 1
          bus info: usb@1:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 3200
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 0344
             serial: 2CAH8M18
             size: 372GiB (400GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=8c87f020
           *-volume
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/MAXTER
                version: 1.0
                serial: 11fa8ec0-bc3f-448a-81e2-d79dcc964817
                size: 372GiB
                capacity: 372GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2007-08-26 20:32:38 filesystem=ext3 label=MAXTER modified=2008-07-04 16:10:58 mount.fstype=ext3 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2008-07-04 16:10:58 state=mounted
     *-scsi:1
          physical id: 2
          bus info: usb@2:2
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: DCP-130C
             vendor: Brother
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdc
             version: 1.00
             capabilities: removable
             configuration: ansiversion=2
           *-medium
                physical id: 0
                logical name: /dev/sdc

---

### Post by hairshirt on 2008-07-04
Just a very little bump :)

---

### Post by hairshirt on 2008-07-04
bump ... any help out there?

---

### Post by hairshirt on 2008-07-04
Am I the only one with an ASUS P5AD2 Premium board here, on these forums? ... or am I missing something.  I thought this hardware was prime linux material ... but noting but silence!

---

### Post by hairshirt on 2008-07-05
bump

---

### Post by hairshirt on 2008-07-05
bump

---

### Post by hairshirt on 2008-07-05
SOLVED

I have solved the major issue for myself.

I simply swaped the cd drives around on the box.

There is one dvd/cd rom (was master now slave) and one dvd/cd burner (was slave now master).  I have just swaped them around (of course master on the end of the cd ribbon).  The cd burner on the system was the one I used to burn the cd - I then removed the cd from that drive and place it in the cd reader.  I'd actually burnt a number of cds on a number of my systems but all to no avail - until i'd swaped the cd drive around as mentioned before and installed 8.04 from the same drive with which it was burnt.

I hope this helps a great many people.

---

### Post by AriLex on 2008-07-11
Weird....
I have the same problem (on an ACER Aspire 3690), so I can try to burn a new CD from live UBUNTU and use that one in the same drive I made it...
Actually I used a cheap DVD, so that might be the problem, however the integrity check said it was ok, as well as the checksum of the .iso

---

### Post by xpu on 2009-10-04
hairshirt... I don't know how you figured this out and what made you switch from slave to master but thank you. Your 3 days of pulling your hair out was worth it coz i'm sure it helped more people than the amount that have thanked you.

For anyone else with this problem:

I am still very new to ubuntu.
I got the initial error when running a live session. It would log out instantly and give some error about session less than 10 seconds. Input/Output error.

So I logged in under Failsafe Gnome session

Then when I tried to install, I got [Errno 5] - googled it, read a few pages.. came accross the hairshirt's post and switched drives. Worked like a charm. Logging into new installation as we speak.. hopefully no errors.......... and viola, no errors.

Thanks

---

### Post by alextrastero on 2010-02-03
Hi there, im really really really new and when installing ubuntu 9.10 it gives me a:
[COLOR=Red]errno5, input/output[/COLOR] error

 - I've tried switching master/slave to the DVD/ROM, but the connection is SATA
 - I've tried a new cd and nothing
 - When i do the "check integrity" option it says: "Check finished: errors found in 1 files!" WHAT DOES THAT MEAN?

I hope i can install ubuntu, im sick of windows!

Thank you

---

### Post by alextrastero on 2010-02-03
SOLVED!!
 - Burned the cd again...

---

### Post by salemboot on 2010-03-20
I believe it must be an issue with Hal/Udev. I thought it odd back when I experienced the problem.

---

