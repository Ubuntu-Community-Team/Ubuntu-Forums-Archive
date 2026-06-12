---
title: "Dell Inspiron B120: a poor upgrade choice or a stupid move"
date: 2015-11-06
forum: Installation &amp; Upgrades
---

### Post by Eanruig on 2015-11-06
I was running Ubuntu 9.04 on a Dell Inspiron B120 as a single user. 

I was using a 250GiB hard drive with six partitions: /boot, swap, /, /home, /var, and /tmp, but I was seeing slow performance, and long pauses, so I thought to upgrade to Lubuntu - the B120 being an older, slower, machine. 

I thought i was doing the upgrade correctly, making a backup before installing Lubuntu 14.1. 

However, after the upgrade finished, I saw that the partitions from Ubuntu were all, except for swap, displayed in the side-panel of Lubuntu file manager as various sizes of separate volumes. 

For example, there is now a 197 GB volume which was the original Ubuntu /home partition - all the Ubuntu /home directories and files are on it, but its location appears as
 
/media/username/f10da0f5-589e-4468-b522-0bdfe43ac772

Now, the problem as I see it is that the greatest part of my hard drive is difficult to get at. 
I would like to reclaim the several partitions under their old names - if possible. 
I thought of using soft links to accomplish that, but am not sure about the wisdom, not to mention the ease, of merging the contents of the Ubuntu partitions with the new Lubuntu file system.

I am inclined to think that I have messed things up rather badly - that's why I gave myself the "stupid move" option in the title. 

Does my idea of soft links seem feasible? 
Am I faced with a re-installation of Lubuntu? 
Or, is there some magic I haven't thought of yet? 

Thanks in advance for suggestions.

Henry IX

---

### Post by sudodus on 2015-11-07
I suggest that you make a new installation of Lubuntu 14.04.1 LTS. Try it live, so that you know that it works, or try other versions until you find which version works for you: 14.04.2, 14.04.3, 15.10 have shorter lifetime (until end of support), but might work better.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

0. You have a backup. Can you access files from it directly, or must you restore the whole system from it? Anyway, I suggest that you make your personal files available. You will need them 'soon' in step #5.

1. Boot a live session from the Lubuntu desktop install system, ***'Try Lubuntu'***.

2. Start ***gparted*** and create a new partition table. If you do not use Windows you can start with a big extended partition and have logical partitions inside it. Then you will not be limited to four partitions. Create logical partitions: A **root** partition, maybe a **home** partition, maybe a **data** partition, and finally a **swap** partition inside the extended partition.

3. Start the installer. Select ***Something else*** at the partitioning window and select the partitions created with gparted. Check that the bootloader will be installed to the correct location (the head of the drive, where you install Lubuntu, probably **/dev/sda**).

4. Boot into your new installed system.

5. Copy your personal files to where you want them in **/home** or in the **data** partition.

---

### Post by mörgæs on 2015-11-07
Some of the B120's have hardware limitations. In order to see if this applies to you please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

I suggest that you change the thread title to **Dell Inspiron B120** or similar. It's more helpful to other users.

---

### Post by efflandt on 2015-11-07
Simplest if you reinstall is to use the mentioned ***Something else*** and when you get to the partitioning part, only set the / partition to format, set other partitions to their desired path, without checking the box to format those other partitions. Then they should automatically end up in your /etc/fstab to mount them in their expected locations.

The other option if you know how to configure /etc/fstab, would be to boot a live/install iso to a live system, rm or mv anything from directories you are going to mount other partitions to (which will be inaccessible when other partitions are mounted there), and modify /etc/fstab to mount your other partitions where you want them. If you do it properly, you should be able to reboot into the system and everything should be where you want it.

---

### Post by Eanruig on 2015-11-07
For mörgæs:

lshw.txt follows -

```

computer
    description: Portable Computer
    product: ME051
    vendor: Dell Inc.
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0TD535
       vendor: Dell Inc.
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A04
          date: 12/22/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.13.8
          slot: Microprocessor
          size: 1400MHz
          capacity: 2130MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx bts
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0
             serial: [REMOVED]
             slot: DIMM_A
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous [empty]
             physical id: 1
             slot: DIMM_B
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
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
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:dff00000-dff7ffff ioport:eff8(size=8) memory:c0000000-cfffffff memory:dfec0000-dfefffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:dff80000-dfffffff
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
             configuration: driver=snd_hda_intel latency=0
             resources: irq:42 memory:dfebc000-dfebffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:20000000-201fffff ioport:20200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:dfc00000-dfdfffff ioport:d0000000(size=2097152)
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:bf80(size=32)
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:bf60(size=32)
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:bf40(size=32)
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:bf20(size=32)
        *-usb:4
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:b0000000-b00003ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:dfb00000-dfbfffff
           *-network:0
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
                resources: irq:18 memory:dfbfe000-dfbfffff
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2915ABG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth1
                version: 05
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=[REMOVED] latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11abg
                resources: irq:17 memory:dfbfd000-dfbfdfff
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD2500BEVE-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1A11
             serial: [REMOVED]
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000420f8
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: [REMOVED]
                size: 953MiB
                capacity: 953MiB
                capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2013-03-26 23:22:18 filesystem=ext3 lastmountpoint=/media/hanraoi/84c3ae8e-bddd-4942-b01f-64546938e368 modified=2015-11-07 00:56:26 mounted=2015-11-06 10:11:31 state=clean
           *-volume:1
                description: EXT3 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 18GiB
                capacity: 18GiB
                capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                configuration: created=2013-03-26 23:49:45 filesystem=ext3 lastmountpoint=/ modified=2015-11-07 07:40:34 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-11-07 07:40:36 state=mounted
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 213GiB
                capacity: 213GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 13GiB
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 9536MiB
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 4767MiB
              *-logicalvolume:3
                   description: Linux swap / Solaris partition
                   physical id: 8
                   logical name: /dev/sda8
                   capacity: 1906MiB
                   capabilities: nofs
              *-logicalvolume:4
                   description: Linux filesystem partition
                   physical id: 9
                   logical name: /dev/sda9
                   capacity: 183GiB
        *-cdrom
             description: DVD reader
             product: CDRWDVD CRX850E
             vendor: SONY
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 5DK1
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc

```

All that information makes my head swim.

Henry IX

---

### Post by sudodus on 2015-11-08
You have

- an Intel(R) Celeron(R) M processor at 1.40GHz and
- RAM size 512MiB
- old Intel graphics: Mobile 915GM/GMS/910GML Express Graphics Controller

A current version of Lubuntu should work with the [boot option](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M) **forcepae**.

[UXA acceleration](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics) might help.

[Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

[More details about Lubuntu and old computers](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

---

### Post by mörgæs on 2015-11-08
512 MB of memory will be a limitation but the processor runs fine with a standard Lubuntu 15.10 and 14.04.3, also without forcepae.

You have a number of old partitions, some of which are built on the old file system ext3. 

I suggest that you back up your important files to an external drive or using some cloud service and install a fresh 15.10, allowing Lubuntu to use the entire hard disk in the process. That will give you partitions built on ext4 and no wasted space.

---

### Post by Eanruig on 2015-12-02
I really appreciate the suggestions given - they helped to direct and concentrate my thinking. What I finally did was to label the several existing partitions - /, /usr, /var, /tmp, & /home and tinker with fstab. Eventually following further apt-get cleans, autocleans, purges, upgrades and installs, the system is running suitably with one residual problem - slowdowns and "not responding". I think I will replace the 512 M RAM with 2 G (max for the B120), and see what more available memory will accomplish. If/when I do upgrade to Lubuntu 15.10, I can follow mörgæs' suggestion of going to ext4.

Henry IX

---

### Post by mörgæs on 2015-12-03
Good. If you consider the problem solved please mark the thread so.

---

