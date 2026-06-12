---
title: "Dell OptiPlex GX260"
date: 2014-12-10
forum: Installation &amp; Upgrades
---

### Post by whvw on 2014-12-10
I have Ubuntu 10.04 running on an old Dell i686 (that began life running Windoze XP). It has been going for years, but now it is getting cranky, and  I want to go to Mint 17. I did a USB install, but it crashes upon reaching the desktop, amid some complaining about graphics cards. A bad install? I tried numerous attempts, and even resorted to an HD loaded with Mint 17 on another machine. Same problem. Tried going to ubuntu 12 but no dice. I get complaints about being unable to munmap, MMap out of room, please increase size of APT, (cannot find any info on how to do that) etc. I read of some "aptitude xxx" commands, tried them with only partial success. I have even wiped the old 10.04 install and done a fresh one, but am still unable to go beyond 10.04. Please help.

---

### Post by grahammechanical on 2014-12-10
I do not support Linux Mint. You must decide what you want to do. Upgrade from Ubuntu 10.04 to Ubuntu 12.04 or install Linux Mint? Either way, this is significant. Do you not think?

> [COLOR=#000000]amid some complaining about graphics cards. [/COLOR]

There are couple of things I wonder about with regards to that card. a) how much of its own memory does it have? Does it use system RAM? b) Do the proprietary video drivers still support that card? I have heard that the makers of video cards are in the habit of dropping support for what they think of as obsolete video cards. I have not heard of the developers of the open source video driver doing that.

Newer versions of Ubuntu will install newer proprietary video drivers if we tick the box "Install third party software" during the installation. Or if we are using a third party (proprietary) video driver at the time we start the upgrade.

You do not tell us about the rest of the hardware in that machine. The fact that it had Windows XP on it is less important than the actual hardware specification. You may need to be trying with one of the flavours of Ubuntu, such as Xubuntu or Lubuntu.

Regards.

---

### Post by mörgæs on 2014-12-11
Yes, we need to know more. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. Can be done in a live boot of 10.04

I have a feeling that we are dealing with really old stuff here but let's take a better look.

---

### Post by whvw on 2014-12-11
Here is the file you requested. Thanks.

```
 computer
    description: Mini Tower Computer
    product: OptiPlex GX260
    vendor: Dell Computer Corporation
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=44454C4C-4E00-104E-8054-B4C04F313331
  *-core
       description: Motherboard
       product: 02X378
       vendor: Dell Computer Corp.
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A06 (04/28/2003)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.7
          slot: Microprocessor
          size: 2666MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_A
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff(prefetchable)
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:e8000000-efffffff(prefetchable) memory:ff680000-ff6fffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ffa00800-ffa00bff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:e000(size=4096) memory:ff800000-ff9fffff
           *-network
                description: Ethernet interface
                product: 82540EM Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: c
                bus info: pci@0000:01:0c.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 1GB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI duplex=full firmware=N/A ip=[REMOVED] latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1GB/s
                resources: irq:18 memory:ff8e0000-ff8fffff ioport:ecc0(size=64)
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:80000000-800003ff
           *-disk
                description: ATA Disk
                product: WDC WD600BB-00CA
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 17.0
                serial: [REMOVED]
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000df6c5
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 53GiB
                   capacity: 53GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2014-12-10 04:36:00 filesystem=ext4 lastmountpoint=/"ï¿œyï¿œï¿œï¿œï¿œï¿œïï¿œï¿œ]ï¿œï¿œï¿œ*ï¿œï¿œï¿œ^ï¿œï¿œïï¿œï¿œh ï¿œï¿œh/ï¿œï¿œ^ï¿œï¿œïï¿œï¿œ!ï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œïï¿œï¿œ^ï¿œï¿œïï¿œï¿œ^ï¿œï¿œ]k modified=2014-12-10 07:27:52 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2014-12-11 12:47:01 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2381MiB
                   capacity: 2381MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2381MiB
                      capabilities: nofs
           *-cdrom:0
                description: SCSI CD-ROM
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio
                configuration: status=nodisc
           *-cdrom:1
                description: DVD reader
                product: RW/DVD GCC-4480B
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: C104
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:dc80(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:d800(size=256) ioport:dc40(size=64) memory:ffa00400-ffa005ff memory:ffa00000-ffa000ff
     *-scsi
          physical id: 1
          bus info: usb@1:6
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 7441MiB (7803MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=c3072e18
           *-volume
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/KINGSTON
                version: FAT32
                serial: [REMOVED]
                size: 7433MiB
                capacity: 7437MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=KINGSTON mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted
```

---

### Post by mörgæs on 2014-12-11
Next time please use CODE tags.

The computer is not that bad. Ubuntu does not like it but Lubuntu 14.* does, especially if you add an xorg.conf. See the link in my signature for details.

An even better option is finding a stronger graphics card.

---

### Post by whvw on 2014-12-11
Thanks for that suggestion, I'll try Lubuntu 14. I did get Ubuntu 14 to install, but man I hate that style of desktop, and it is slooooooooooooow! Some windows take 10 or more seconds to display. I actually liked 10.04 a lot, (after I customised it) and would be happy to keep it if it was still fully functional, (software centre, etc.). 
As for the computer, I believe the graphics "card" is built into the motherboard on that machine, I don't think that you can just pop in another. Hopefully I'm wrong on that, (possibly Mint 17 would then work).
Stupid question time: Just what is a "code tag" anyway? I would have used them if I had known what they are.

---

### Post by mörgæs on 2014-12-12
> **whvw said:**
> 
As for the computer, I believe the graphics "card" is built into the motherboard on that machine.

Correct.

> **whvw said:**
> 
I don't think that you can just pop in another. 

Yes you can, if the slot fits. Have you taken a look inside the case? 


> **whvw said:**
> 
Just what is a "code tag" anyway? I would have used them if I had known what they are.

As you can see above they make terminal output easier to read. Look for the # button in the advanced editor and push Preview to see the results.

---

### Post by whvw on 2014-12-12
Inside the machine there are plenty of slots. I'll get my hands on a new-er graphics card and see if the machine likes it.

 As for Lubuntu, I loaded it up, and so far I think it's great! It doesn't flow as easily as Mint 17, but it works well (and) looks good, many orders of magnitude better than the straight Ubuntu 14.04 in both aspects. There are two funnies, though: in Firefox, I get solid bars instead of the URL I put in, and I can't change the _terminal's_ date format.

Thanks.

---

### Post by sudodus on 2014-12-13
Try according to this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics)

Edit (or create) **/etc/X11/xorg.conf** as follows: (there should be a **tab** before each line except the first and the last). 

```
Section "Device"
        Identifier "Intel Graphics"
        Driver "intel"
        Option "AccelMethod" "uxa"
EndSection
```

Restart X (reboot, restart your display manager, whatever). Colors are back to the way they used to be and flash works.

---

