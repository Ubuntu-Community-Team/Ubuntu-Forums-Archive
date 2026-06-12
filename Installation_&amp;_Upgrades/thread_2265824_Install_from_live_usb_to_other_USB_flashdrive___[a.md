---
title: "Install from live usb to other USB flashdrive   [and then to SSD]"
date: 2015-02-18
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2015-02-18
I am installing Ubuntu from a live usb to a 32Gb usb flashdrive
when i get to the second photo here it throws the "No Root File System"
message you see here

[ATTACH=CONFIG]260053[/ATTACH][ATTACH=CONFIG]260054[/ATTACH]


What are the next steps?  Please explain carefully step by step as I am not very au fait with installing this way
PS i want the bootloader on the 32Gb too so i can pick usb from the bios once installed




thanx   shan

---

### Post by sudodus on 2015-02-18
0. ***Backup*** what is important to keep, because installing operating systems is risky.

Do you want Ubuntu installed (an installed system like it were installed into an internal drive)? Then I suggest that you select to install into the whole drive.

1. Remove the internal drive(s). It will remove the risk that you touch the internal drive(s) by mistake.

Things are slower from USB than from an internal drive. For this reason you should be prepared to select a lighter desktop environment than what you use for the internal drive, so try Xubuntu and Lubuntu (and standard Ubuntu for comparison). See this link 'Notes about speed' [https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

2. [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")                 

3. Start installing: At the installer's partitioning window, select Install to the whole drive (which will overwrite what was there before).

This should 'do it' in a straight-forward way (answer the questions and give the information requested ...).

-o-

If you don't want to remove the internal drive, things will be more complicated in order to install the operating system and the bootloader to the correct drive. In this case you must select ***Something else*** at the installer's partitioning window. (I do not describe it now, because I hope that you select the other method.)

---

### Post by nerdtron on 2015-02-18
Removing the internal drives is definitely safer. But if you really want to go ahead and install on the 32GB usb drive, here goes.

Select sdc1 and delete it using the minus sign. (all data from it will be erased).
Select the free space you created and click the plus sign. Create a partition that is about 29GB and assign it as ext4 file system, mount point is "/" and check format. Then the remaining free space Probably about 1.5GB, double click and set it as "swap area".


On the lower part of the installer, be sure the boot loader is /dev/sdc. Post a screenshot again here if you are not sure. 

You should be able to proceed now.
I hope you have a general idea here on what is happening on your partitions

---

### Post by shantiq on 2015-02-18
thanx guys   going to try Nerdtron's route here [would never have guessed or intuited any of this]and thanx to Sudodus for suggesting i remove internal drive .   i shall try and make sure sda is NEVER clicked on at any stage and LXDE is always my choice these days
so here goes  ...    will see if i succeed   ....     i want to do this to see if there is any point in getting a 64Gb or 128Gb external ssd to do same

experiments really!

---

### Post by sudodus on 2015-02-18
Watch out with the bootloader! You must ***actively*** point it to the USB drive, otherwise it will be installed into the internal drive.

Good luck :-)

---

### Post by shantiq on 2015-02-18
Thanx Sudodus   I had seen this and was mindful of that danger

I now see why you suggested removing the HDD first

I picked Bodhi Linux for this as very light

and this is where i got to

But it wants interfere with the sda partition internal HDD [and probably destroy my main install therefore] so i wonder if there is a way to not have that happen WITHOUT having to remove HDD

Photo explains it all >>


[ATTACH=CONFIG]260057[/ATTACH]

---

### Post by sudodus on 2015-02-18
You can use the ***Something else*** window to tell the installer to not use that swap partition in the internal drive. Click on the line for that partition and select 'Do not use' or some similar text. Save it and go ahead.

---

### Post by nerdtron on 2015-02-18
Double click the swap on /dev/sda and check the option "do not use" this partition.

---

### Post by shantiq on 2015-02-18
well thanx to both of you    loaded a treat

Bodhi Linux was not telling me how it was going so loaded 14.04 32-bit in the end

and it is **no slower** then the HDD    and **completely silent **of course and gives me access to my 500Gb HDD which i can use as a storage unit now and a backup    so ace   


Now the next step of my cunning plan is to buy an [external SSD]("http://www.amazon.co.uk/Verbatim-47622-128GB-USB-External/dp/B008OE0S56/ref=sr_1_1?ie=UTF8&qid=1424291104&sr=8-1&keywords=external+ssd") and do the same
Will it install on the SSD as it does on a USB flashdrive?    is there anything else i should be aware of?

again thank you for help   much appreciated !    shan

---

### Post by sudodus on 2015-02-18
Yes, it will install and run in a similar way. If you can connect the external SSD via eSATA or USB 3, it will be much faster than with USB 2.

---

### Post by shantiq on 2015-02-18
> **sudodus said:**
> Yes, it will install and run in a similar way. If you can connect the external SSD via eSATA or USB 3, it will be much faster than with USB 2.


Thank you i recently added USB3 ports to my computer but those are not seen by BIOS so i cannot boot from there


how to do that? add new ports to BIOS?


will mark this one here as solved and start a new thread with this question

---

### Post by ubfan1 on 2015-02-18
The SSD will just be another drive as far as the installer is concerned.  Ensure any USB SSD drive you purchase supports the TRIM function -- just putting an SSD into a ramdom USB hard disk enclosure will work, but may not support TRIM ;^(  Take a look around for the optimization/speedup questions/answers for flash drives, and apply those suggestions to the SSD setup (if you can spare the ram).

---

### Post by mc4man on 2015-02-18
> **shantiq said:**
> well thanx to both of you    loaded a treat

Bodhi Linux was not telling me how it was going so loaded 14.04 32-bit in the end

and it is **no slower** then the HDD    and **completely silent **of course and gives me acces to my 500Gb HDD which i can use as a storage unit now and a backup    so ace   


Now the next step of my cunning plan is to buy an [external SSD]("http://www.amazon.co.uk/Verbatim-47622-128GB-USB-External/dp/B008OE0S56/ref=sr_1_1?ie=UTF8&qid=1424291104&sr=8-1&keywords=external+ssd") and do the same
Will it install on the SSD as it does on a USB flashdrive?    is there anything else i should be aware of?

again thank you for help   much appreciated !    shan

I've only been running Ubuntu thru an external ssd for last 18 months or so. This is via usb3
The first one which was extremely fast & expensive is currently completely borked, may have been some internal failure or because I made the unfortunate choice to do a full format on (I'd say a full format on an ssd is a poor thing to do.
[http://www.angelbird.com/en/prod/ssd2go-154/](http://www.angelbird.com/en/prod/ssd2go-154/)

Now i'm using a less expensive one, it's doing fine  still after a few months.  [http://www.amazon.com/gp/product/B00FYIXA32/ref=oh_aui_detailpage_o02_s00?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B00FYIXA32/ref=oh_aui_detailpage_o02_s00?ie=UTF8&psc=1)
not quite as fast but still very good

If I get another laptop then it will have to have an eSATA port as that is better for ext. ssd's for various reasons.

(here I do add noatime to fstab for the ssd, don't use a swap at all but certainly not on the ssd & try to avoid unneeded writes & deletes on the ssd.

---

### Post by shantiq on 2015-02-18
thanx for input      will go for a [cheaper option]("http://www.amazon.co.uk/Verbatim-47622-128GB-USB-External/dp/B008OE0S56/ref=sr_1_1?ie=UTF8&qid=1424291104&sr=8-1&keywords=external+ssd") to start with or something for the same money i can get locally

no eSATA on my 10-year old machine but i have installed 4 USB 3.0 ports recently    **but the bios does not see them as yet** so how is one to make them visible to a ten-year old bios if possible?  so i can boot the SSD when i have it from there and not from a USB 2.0 slot


any of you here would know that/?      not sure whether i should start a new thread with this or keep it here?


shan

---

### Post by sudodus on 2015-02-19
I know that it can be difficult to boot from USB 3, if it has been added afterwards. If you have a desktop computer or workstation, it is very easy and cheap to add an eSATA port (I have added such equipment to several computers). See this link

[http://www.akasa.com.tw/update.php?tpl=product/product.detail.tpl&no=181&type=Cables&type_sub=SATA%20Cable%20Adapters&model=eSATA-45-EX](http://www.akasa.com.tw/update.php?tpl=product/product.detail.tpl&no=181&type=Cables&type_sub=SATA%20Cable%20Adapters&model=eSATA-45-EX)

---

### Post by shantiq on 2015-02-19
thanx for that sudodus and all your other sterling advice.   Might be the missing piece of kit i need here   

but do i need to have eSATA   inside already  ?  not sure that i do   [2005 machine]


sudo lshw

```
description: Desktop Computer    product: 00000000000000000000000 (To Be Filled By O.E.M.)
    vendor: Packard Bell NEC
    version: PB34225301
    serial: 049652320227
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=549D0B9A-BE69-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: MS-7168
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012
          date: 09/06/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.15.2
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1800MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow extd_apicid pni lahf_lm vmmcall cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci:0
          description: Host bridge
          product: RS480/RS482/RS485 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS4xx PCI Express Port [ext gfx]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:7000(size=4096) memory:fc500000-fe6fffff ioport:bbf00000(size=603979776)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 8400 GS Rev. 3]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:7c00(size=128) memory:fe680000-fe6fffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:18 memory:fe67c000-fe67ffff
        *-pci:1
             description: PCI bridge
             product: RC4xx/RS4xx PCI Express Port 3
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 memory:fe700000-fe7fffff
           *-usb
                description: USB controller
                product: VIA Technologies, Inc.
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:18 memory:fe7ff000-fe7fffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:23 ioport:bc00(size=8) ioport:b800(size=4) ioport:b400(size=8) ioport:b000(size=4) ioport:ac00(size=16) memory:febffc00-febffdff memory:feb00000-feb7ffff
        *-ide:1
             description: IDE interface
             product: IXP SB4x0 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=16) memory:febff800-febff9ff memory:fea80000-feafffff
        *-usb:0
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:febfe000-febfefff
        *-usb:1
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:febfd000-febfdfff
        *-usb:2
             description: USB controller
             product: IXP SB4x0 USB2 Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:febfc000-febfcfff
        *-serial
             description: SMBus
             product: IXP SB4x0 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16) memory:bb000000-bb0003ff
        *-ide:2
             description: IDE interface
             product: IXP SB4x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-isa
             description: ISA bridge
             product: IXP SB4x0 PCI-ISA Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: IXP SB4x0 PCI-PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:8000(size=4096) memory:fe800000-fe8fffff
           *-network:0
                description: Ethernet interface
                product: RTL8169 PCI Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:03:01.0
                logical name: eth1
                version: 10
                serial: 00:0a:cd:26:64:71
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=82.20.25.138 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
                resources: irq:9 ioport:8800(size=256) memory:fe8ffc00-fe8ffcff memory:fe8c0000-fe8dffff
           *-network:1
                description: Ethernet interface
                product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:03:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:b6:0d:bb
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 ioport:8400(size=256) memory:fe8ff800-fe8ff8ff memory:fe8e0000-fe8effff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:03:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:9 memory:fe8ff000-fe8ff7ff ioport:8c00(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=snd_atiixp latency=64 mingnt=2
             resources: irq:17 memory:febff400-febff4ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3500630AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 5QG10JMC
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00021cfa
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/shantiq/739e22d6-04f7-42f0-89e9-7e99603d63b3
                version: 1.0
                serial: 739e22d6-04f7-42f0-89e9-7e99603d63b3
                size: 463GiB
                capacity: 463GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-20 10:25:55 filesystem=ext4 lastmountpoint=/media/shantiq/739e22d6-04f7-42f0-89e9-7e99603d63b3 modified=2015-02-19 08:26:37 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2015-02-19 08:26:37 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2557MiB
                capacity: 2557MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2557MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD_RW ND-3550A
             vendor: _NEC
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.52
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@1:5
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Innostor
             vendor: Innostor
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 1.00
             serial: 000000000000000089
             size: 29GiB (31GB)
             capabilities: removable
             configuration: ansiversion=6 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 29GiB (31GB)
                capabilities: partitioned partitioned:dos
                configuration: signature=0003cdb0
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: 8971e9a3-720b-4946-8d88-86d1cfa33a06
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2015-02-18 13:37:46 filesystem=ext4 lastmountpoint=/ modified=2015-02-19 08:24:40 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-02-19 08:24:40 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   logical name: /dev/sdb2
                   size: 2816MiB
                   capacity: 2816MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 2816MiB
                      capabilities: nofs
     *-scsi:3
          physical id: 5
          bus info: usb@2:4
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@7:0.0.1
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@7:0.0.2
             logical name: /dev/sde
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@7:0.0.3
             logical name: /dev/sdf
             configuration: sectorsize=512
     *-scsi:4
          physical id: 6
          bus info: usb@1:6.2
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: DVD-RAM writer
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sr1
             capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: status=nodisc



```

---

### Post by sudodus on 2015-02-19
That particular eSATA hardware connects internally to SATA, so you need standard SATA connections inside. If you have old IDE alias PATA connections (wide connectors and often wide flat cables) it does not work with eSATA. According to your list you have serial ATA alias SATA, so it should work :-)

```
        *-ide:0
             description: IDE interface
             product: IXP SB400 **[COLOR=#006400]Serial ATA Controller[/COLOR]**
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:23 ioport:bc00(size=8) ioport:b800(size=4) ioport:b400(size=8) ioport:b000(size=4) ioport:ac00(size=16) memory:febffc00-febffdff memory:feb00000-feb7ffff
        *-ide:1
             description: IDE interface
             product: IXP SB4x0 **[COLOR=#006400]Serial ATA Controller[/COLOR]**
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=16) memory:febff800-febff9ff memory:fea80000-feafffff


```

---

### Post by shantiq on 2015-02-19
ok brill 

[and is this the same]("http://www.maplin.co.uk/p/sata-ii-2-external-esata-and-2-internal-sata-pci-express-card-a35fk") thing as the one you linked but more involved?   

or else [here]("http://www.amazon.co.uk/Akasa-ESATA-45-EX-SATA-eSATA-Adapter/dp/B004QIG9FW/ref=sr_1_6?ie=UTF8&qid=1424340279&sr=8-6&keywords=akasa+eSATA+adapter")     it shows in the picture where to plug it     

i[IMG]http://www.raid10recovery.info/sata-ports.jpg[/IMG]

---

### Post by sudodus on 2015-02-19
Yes, but the more involved card is more expensive, and might not be available for booting (maybe similar problem as with the USB 3 card).

---

### Post by shantiq on 2015-02-19
ha ok   so will get[ this]("http://www.amazon.co.uk/Akasa-ESATA-45-EX-SATA-eSATA-Adapter/dp/B004QIG9FW/ref=sr_1_6?ie=UTF8&qid=1424340279&sr=8-6&keywords=akasa+eSATA+adapter")



PS had a good look inside my machine and it plugs here i think

[ATTACH=CONFIG]260082[/ATTACH]


one question remains: ssd come with a usb lead but do they also have a sata lead to plug in that socket at the back or do we need to get that separately? thanx for all your info

---

### Post by sudodus on 2015-02-19
A standard SSD is made for internal connection to SATA. You can put such a 'mass storage device' into a box for using externally. Such a box can have eSATA and USB 2 or USB 3 connections, for example this one:

[http://www.akasa.com.tw/update.php?tpl=product/product.detail.tpl&no=181&type=Enclosures&type_sub=2.5%20Enclosure&model=AK-TL2SEB-BK](http://www.akasa.com.tw/update.php?tpl=product/product.detail.tpl&no=181&type=Enclosures&type_sub=2.5%20Enclosure&model=AK-TL2SEB-BK)

There are several similar boxes, but I have such a box, and I know that it works with SSD and eSATA.

If you get an SSD for external use, you should make sure that there is an eSATA connection, but it might be hard to find 'such animals'.

---

### Post by shantiq on 2015-02-19
ok so [get this ]("http://www.amazon.co.uk/Akasa-AK-TL2SEB-BK-inch-Lokstor-Enclosure/dp/B0098WEQ7E/ref=sr_1_1?ie=UTF8&qid=1424348331&sr=8-1&keywords=Lokstor+X21")   which has [COLOR=#333333][FONT=Arial]USB 3.0 and eSATA connectivity [/FONT][/COLOR]and place any SSD inside    and plug at the back of computer with [this]("http://www.amazon.co.uk/Akasa-ESATA-45-EX-SATA-eSATA-Adapter/dp/B004QIG9FW/ref=sr_1_6?ie=UTF8&qid=1424340279&sr=8-6&keywords=akasa+eSATA+adapter")

and that is the way forward?  if i understand it all


thanx    brilliant

---

### Post by sudodus on 2015-02-19
Yes

---

### Post by shantiq on 2015-02-26
Right so got my sata adaptor and my Akasa box and inside i have placed a Crucial 128Gb SSD

i fired my live-usb with 14.04 and got to this screen[ATTACH=CONFIG]260294[/ATTACH]

the SSD is seen as sdb   but the plus and minus signs are blanked out


Does the SSD need to be formatted with gnome-disks before i do this install?


How do i proceed here ?    thanx    shan


gnome-disks shows this >>>


[ATTACH=CONFIG]260295[/ATTACH][ATTACH=CONFIG]260296[/ATTACH]

ps    also the crucial does not appear as a mounted volume    might this be the problem and how do i corrext this?    thanx


[ATTACH=CONFIG]260298[/ATTACH]


ps2      bios sees ssd as a potential booting option so that is good news    [once Ubuntu is on there]

---

### Post by sudodus on 2015-02-26
It is probably easiest if you ***remove your internal drive*** and 'Use the entire disk'.

The second easiest method is to use ***gparted*** to create the partitions you want. It has a better graphical interface. Create a new partition table if necessary, and create a big root partition and a small swap partition. And after that run the ***installer*** and select ***Something else***.

---

### Post by shantiq on 2015-02-27
thanx S   will try method one first ;   just needs to be unplugged i guess not actually removed right?


**EDIT:  **   thank you Sudodus for all your kind help.  For £95 all in [sata adaptor /caddie/ ssd]   it is way faster and TOTALLY silent; which on a ten-year old machine seems surreal.   Should have done this long ago

ps    
1.   unplugged hdd inside [takes 2 minutes]
2.   live-usb to load OS to ssd
3.   replug hdd as storage unit

had to toggle bios order of booting to get all this to happen but was not too hard; now have set ssd as 1st boot

---

### Post by sudodus on 2015-02-27
Congratulations :KS

---

