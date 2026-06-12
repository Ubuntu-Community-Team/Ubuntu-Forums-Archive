---
title: "CHALLENGE: Upgrade to latest Ubuntu"
date: 2015-09-18
forum: Installation &amp; Upgrades
---

### Post by Cabal2122 on 2015-09-18
Here is the challenge. 

Hardware: Toshiba NB255. A ZTE700 Smart Phone, 32 gb Micro Card. 1TB Silicon Power Hard Drive, Important files that can not be deleted. Figure 80 gb left on in. 

I wish to update my Net book to the latest version of Ubuntu. It currently runs 11.04. Classic gnome. ;) I can connect to the Internet, repositories no longer work nor does the update button for the applications manager. I have Brasero disk burner installed but no DVD drive installed. I have zero cash and access to only this computer and the smart phone (my real name is Oscar and I live in a trashcan). The smart phone runs Android Jelly Bean.

How do you make this work? If you can install Linux on a potato, this should be no problem for this crew. :popcorn:

******************EDIT****************
here are the specs for the PC, totally zoned out on adding this. my fault. 

```
minigod                   
    description: Notebook
    product: TOSHIBA NB255
    vendor: TOSHIBA
    version: PLL2PU-00701F
    serial: YA077465K
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=1 uuid=84E05D19-DE9A-11DF-95B1-88AE1DFA2094
  *-core
       description: Motherboard
       product: PAV10 DDR2
       vendor: TOSHIBA
       physical id: 0
       version: 1.00
       serial: 0123456789AB
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.60 (07/30/2010)
          size: 99KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.10
          serial: 0001-06CA-0000-0000-0000-0000
          slot: U2E1
          size: 1667MHz
          capacity: 2048MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm cpufreq
          configuration: id=1
        *-cache
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
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
          physical id: c
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: M1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR Synchronous 667 MHz (1.5 ns) [empty]
             physical id: 1
             slot: M2
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: N10 Family DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:f0200000-f027ffff ioport:18d0(size=8) memory:d0000000-dfffffff memory:f0000000-f00fffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0280000-f02fffff
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
             resources: irq:46 memory:f0300000-f0303fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:40000000-401fffff ioport:40200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:4000(size=4096) memory:f0100000-f01fffff ioport:40400000(size=2097152)
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlan0
                version: 01
                serial: 4c:ed:de:4e:a8:33
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.35-24-generic firmware=N/A ip=192.168.1.49 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f0100000-f010ffff
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:40600000-409fffff ioport:f0500000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 05
                serial: 88:ae:1d:fa:20:94
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:43 ioport:2000(size=256) memory:f050c000-f050cfff memory:f0508000-f050bfff
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:40a00000-40a003ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
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
             product: N10/ICH7 Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:18e8(size=8) ioport:18dc(size=4) ioport:18e0(size=8) ioport:18d8(size=4) ioport:18c0(size=16) memory:40a00400-40a007ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK1665GS
                vendor: Toshiba
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: GH01
                serial: 70N1D04YB
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=3125ebe5
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 365e-1e13
                   size: 1498MiB
                   capacity: 1500MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-05-24 20:36:51 filesystem=ntfs label=System state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 7676141b-8511-644e-b712-ef8c13374e1c
                   size: 46GiB
                   capacity: 46GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-05-24 20:37:53 filesystem=ntfs label=TI105860W0F state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: aaaa-61d9
                   size: 7952MiB
                   capacity: 7970MiB
                   capabilities: primary hidden ntfs initialized
                   configuration: clustersize=4096 created=2010-05-24 20:38:57 filesystem=ntfs label=HDDRECOVERY state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 93GiB
                   capacity: 93GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 90GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 2998MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18a0(size=32)
     *-scsi:0
          physical id: 1
          bus info: usb@1:4
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
     *-scsi:1
          physical id: 2
          bus info: usb@1:5
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Silicon-Power
             vendor: PHD 3.0
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdc
             version: 0
             serial: D100#313001145331131
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=6 signature=28b543a6
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/SP PHD U3
                version: 3.1
                serial: 1c2b3807-9a2f-de4b-86fe-4e8d79d9a68f
                size: 931GiB
                capacity: 931GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-12-27 20:17:06 filesystem=ntfs label=SP PHD U3 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
  *-battery
       description: Lithium Ion Battery
       product: PA3395U
       vendor: TOSHIBA
       physical id: 1
       version: 12/01/2005
       serial: 3658Q
       slot: 1st Battery
       capacity: 31500mWh
       configuration: voltage=14.8V
```

---

### Post by Bucky Ball on 2015-09-18
Welcome. Has it got two USB slots or have you got a USB hub? If so, create a bootable USB of 14.04 LTS, boot from it, when you get to the options choose 'Try Ubuntu', back-up any files you don't want to use to an external device. Do a clean install of 14.04 LTS. There is no upgrade ('update' is the wrong terminology for what you want to do and I have changed the thread title accordingly for clarity) option from 11.04 to any supported release via the machine (net).

You could also boot from the Live USB, Try Ubuntu, launch Gparted and resize partitions as needed then install Ubuntu and choose 'Something Else' when you get to the partitioning section of the install. This option is a possibility if you don't have an external drive to save your personal data to.

The challenge is making sure you upgrade the OS before it goes that far out of support in future. 14.04 LTS is a long-term support release and supported until 2019 which is why I'm recommending it as it might suit your style. The interim releases are now supported for nine months only. :)

---

### Post by Cabal2122 on 2015-09-18
Ah thank you Bucky Ball, that is helpful advice. I have 3 USB slots. However I do not have a USB device on hand. In theory I may be able to happen across one. I also am restricted on the programs I can use. I do not have UNetBootin installed. Is there any method in creating a bootable USB device from 11.04 to allow for this work? Keep in mind I can not install new software from repositories (to my limited knowledge). They no longer function for it is sadly no longer 2011. Also just we are clear, I found this thing after someone threw it away in my trashcan. :lolflag: Your help is much appreciated!

---

### Post by grahammechanical on 2015-09-18
You forgot to tell us if that trash can you live in has a connection to an Internet Service Provider. If it does not then you have two options: #1 wait for someone to throw away but into your trash can a USB memory stick with Ubuntu installed on it. #2 Buy one.

If you are able to get an internet connection by means of that smart phone, or some other means, then you can use the web browser in Ubuntu 11.04 to download Ubuntu 14.04.3 ISO image. And then follow this guide.

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

I am sure that Ubuntu 11.04 has Startup Disk Creator.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Also, there is a way to do an End of Life upgrade. It can work, it is "fingers crossed" time.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Back up your data.

Regards.

---

### Post by Bucky Ball on 2015-09-18
As above. :)

---

### Post by coffeecat on 2015-09-18
> **Cabal2122 said:**
> Is there any method in creating a bootable USB device from 11.04 to allow for this work?

Yes, there is an alternative application that is already installed in 11.04 other than the Startup Disk Creator that grahammechanical mentioned. SDC is probably your best bet but a few years ago there was a bug in it which meant it couldn't create a startup disk for a version of Ubuntu other than the version it was running on. Which was a bit silly when you think about it! :) I believe that was fixed long before 11.04 came out, but just in case you find that SDC doesn't work for you, the alternative is the terminal app dd. 

Now before someone intervenes telling you that dd destroys disks, causes global warming, eats live puppies and is to be avoided like the plague, let's get it into context. dd will do exactly what you tell it to. Trouble is, if you make an error in the command, it will do exactly what you told it to, not what you thought you had told it to! 

The ISO file for all releases of Ubuntu for some years now has been designed so that they can simply be dd'd directly to a USB flash drive to create a bootable drive. You don't even have to format or partition the flash drive. I've used dd for every new version of Ubuntu - and some of the development release milestones - for ages now, and it has never let me down. So, assuming that...

[list][*]You have acquired a USB drive which you can use for creating a bootable installation/live medium.
[*]That you have access to a separate external USB drive for backing up your important files.
[*]That you are able to download an ISO of a supported version of Ubuntu in your 11.04 system.
[*]That you know the administrator password for your account.
[/list]

You should have what you need.

In essence you download the ISO, open a terminal and cd to the folder where you have downloaded to, determine the device name of the USB flash drive you want to use as the bootable medium, and then run the following command but modified for your situation:

```
sudo dd if=filename_of_iso.iso of=/dev/sdx
```

Where the x in sdx is b or c or whatever the device name for your USB device is. If you make a mistake in the command, dd will blithely write the ISO filesystem to the wrong device - hence its iffy reputation.

If you find Startup Disk Creator doesn't work for whatever reason, post back and we can clarify the details of the dd command you could use.

---

### Post by Cabal2122 on 2015-09-18
@Grahmmechanical =Fantastic advice! It was really close to success. So I don't have a USB device but I do have the 1TB external hard drive. I attempted to write the ISO to the drive with the program mentioned. However a critical failure occurred. The program could not install the boot manager. So upon restarting the netbook, I find it can not load anything and prompts me to restart the device again and boot into the native OS. Very close but not quite. As for legacy upgrades, it seems I may not be able to perform these, I have no access to the repositories. 

@ CoffeeCat = Very interesting advice. I heard of dd before but was indeed dissuaded from its powers. So I never thought to look into much. Now my question for you is this. If I where to attempt to use the external hard drive with dd would it wipe the data on it that I wish to keep? Could it install the boot manager on the device?

These are very clever things you all are hitting on. I thank you for your time! :KS

---

### Post by Bucky Ball on 2015-09-18
If you have one, better to use a USB for dd and cut down the risk factor. Not sure that you can boot the live installer from a hard drive in any case. I'll leave that to more knowledgeable members.

---

### Post by Cabal2122 on 2015-09-18
@ Bucky Ball = You rock man, thank you for your assistance. If I happen upon a USB device I will indeed attempt it. ^_^

---

### Post by deadflowr on 2015-09-18
> Not sure that you can boot the live installer from a hard drive in any case.

You can if you have grub installed.
It requires knowing where the iso files is and directing a custom grub file to it.
Reference point here: [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
If in anyway that's what you mean.

I actually ran this type of setup with some development release some time ago, also using zync to update the daily-build iso.
(I was sick of re-burning/ re-copying to disk/stick, at the time)

That's all just a* fer what it's worth* anyway, and probably moot.

---

### Post by coffeecat on 2015-09-18
> **Cabal2122 said:**
> Now my question for you is this. If I where to attempt to use the external hard drive with dd would it wipe the data on it that I wish to keep?

Yes. You do not want to dd an Ubuntu iso image to a device that you wish to use as a backup drive. As others have said, keep your external HD for backups and find yourself a separate USB flash drive to make the bootable device. An Ubuntu ISO is only about 1GB in size, so a 2GB flash drive will be ample. Anything bigger would simply be wasted space.

If you were to dd the ISO to an external hard drive, you would probably end up with a bootable device (probably - I've never tried it) but with masses of unusable space on it.

---

### Post by Bucky Ball on 2015-09-19
Yep, dd will give you a live installer bootable USB. The format is done as part of the dd. :)

---

