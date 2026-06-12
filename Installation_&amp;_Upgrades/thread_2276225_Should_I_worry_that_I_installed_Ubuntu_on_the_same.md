---
title: "Should I worry that I installed Ubuntu on the same disk that has windows 7 on it?"
date: 2015-05-01
forum: Installation &amp; Upgrades
---

### Post by Paneesh on 2015-05-01
I installed Ubuntu yesterday, on the same disk (C: drive) that has windows 7 on it (using wubi). Everything is running smooth, but is it prone to errors to install Ubuntu and Windows on the same partition?
Or should I have created a new partition just for Ubuntu?

---

### Post by sudodus on 2015-05-01
Welcome to the Ubuntu Forums :-)

No you should not worry that you installed Ubuntu on the same disk as Windows is installed. It is the most common location of Ubuntu in dual boot systems simply because most people have only one internal disk.

But you should worry about wubi. It is no longer developed or maintained, and even when it was (years ago), wubi was only intended for testing. A wubi system is not as stable as a real installed Ubuntu system. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229766"]
Forums Staff recommendations on WUBI[/URL]

I suggest that you try Ubuntu live and after that decide how to install it (probably a dual boot system). If you have two disks, it is cleaner and easier to succeed to install Ubuntu to the other disk (not the one with Windows). In that case it is easier and less risky to disconnect the Windows disk while installing. See also the following link
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by Paneesh on 2015-05-01
Thanks a lot for your reply!

I'm totally a newbie when it comes to installing new operating systems, disk partitioning and stuff!
It'd be really helpful if you help me walk through to re-install Ubuntu from the start without using wubi (as it is no longer supported) alongside windows!
I have a Ubuntu CD with .iso file in it to install that!
But could you please help me??

---

### Post by sudodus on 2015-05-01
Please start by making a good backup of everything, that is valuable in the Windows system: personal files (documents, pictures, video clips ...), and also Windows. You can make specific backup copies including a Windows recovery disk, or you can make a complete compressed image of the current system with Windows.

Then you can start the installation - installing operating systems is risky. It works well most of the time, but not always ...

To make it easier to help, please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Boot into the wubi system or from the DVD disk and please post the output of the following commands between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

Start a terminal window with the hotkey combination

***ctrl + alt + t***

type the commands and launch it with the Enter key.

```
sudo parted -l
```

"... space minus ell"

```
df
```

If you don't know how to get information about the computer hardware, you can run the following commands

```

sudo -s  # start running with superuser privileges
lshw -sanitize > lshw.txt
exit    # exit from superuser privileges

```

and attach the file **lshw.txt** or put its content within [noparse][code] tags[/noparse] in the reply

---

### Post by Paneesh on 2015-05-01
elfy - removed attachement, included detail in post

```

computer
    description: Desktop Computer
    product: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=[REMOVED]
  *-core
       description: Motherboard
       product: G41M-VS3
       vendor: ASRock
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.20
          date: 05/31/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Pentium(R) Dual-Core  CPU      E5700  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: [REMOVED]
          slot: CPUSocket
          size: 3GHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
          configuration: cores=2 enabledcores=2 id=1 threads=2
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
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back unified
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
          physical id: d
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: [REMOVED]
          size: 3GHz
          capabilities: vmx ht
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
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fd000000-febfffff ioport:de000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 8400 GS]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff memory:de000000-dfffffff ioport:ec00(size=128) memory:fe000000-fe07ffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:04:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:febfc000-febfffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:fcefc000-fcefffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:80000000-803fffff ioport:ddf00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:d000(size=4096) memory:fcf00000-fcffffff ioport:80400000(size=2097152)
           *-network
                description: Ethernet interface
                product: AR8132 Fast Ethernet
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: c0
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:44 memory:fcfc0000-fcffffff ioport:dc00(size=128)
        *-usb:0
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c480(size=32)
        *-usb:1
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c800(size=32)
        *-usb:2
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c880(size=32)
        *-usb:3
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:cc00(size=32)
        *-usb:4
             description: USB controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fcefbc00-fcefbfff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
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
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:c400(size=8) ioport:c080(size=4) ioport:c000(size=8) ioport:bc00(size=4) ioport:b880(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000AAKX-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 15.0
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=fff7fff7
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /host
                version: 3.1
                serial: [REMOVED]
                size: 78GiB
                capacity: 78GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-07-22 23:03:43 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 387GiB
                capacity: 387GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 156GiB
              *-logicalvolume:1
                   description: HPFS/NTFS partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 211GiB
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 16GiB
              *-logicalvolume:3
                   description: Linux swap / Solaris partition
                   physical id: 8
                   logical name: /dev/sda8
                   capacity: 2046MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 3
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH22NS70
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: EX00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

```

---

### Post by Paneesh on 2015-05-01
RAM: 2GB
Graphic Card: Nvidea 512mb
Hard Disk: 500GB

---

### Post by sudodus on 2015-05-01
It looks promising :-) You have an extended partition and several logical partitions. It looks like you have installed or tried to install a linux system before, because you have a linux file system and a swap partition.

              ```
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 16GiB
              *-logicalvolume:3
                   description: Linux swap / Solaris partition
                   physical id: 8
                   logical name: /dev/sda8
                   capacity: 2046MiB
                   capabilities: nofs


```The following (/host) shows that you are running wubi:

           ```
*-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /host
                version: 3.1
                serial: [REMOVED]
                size: 78GiB
                capacity: 78GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-07-22 23:03:43 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
```

The nvidia card will probably run better with a proprietary driver particularly if you want to play high definition video, but that can wait, because it seems to run well with the built-in driver 'nouveau'.

-o-

Now, please decide where you want to install Ubuntu! It is possible in the 16 GiB linux partition, particularly if you intend to keep data files in other partitions. (Otherwise, you may want to have a little more disk space for it). The existing swap partition is OK.

You may want to try not only standard Ubuntu but also Xubuntu (with a medium light desktop environment, that might run better with your hardware). Try them live and compare before deciding what to install!

---

### Post by Paneesh on 2015-05-01
And you've mentioned,
"If you have two disks, it is cleaner and easier to succeed to install Ubuntu to the other disk (not the one with Windows). In that case it is easier and less risky to disconnect the Windows disk while installing."

So what does it mean to have "two disks? :)
Is lt like partitioning a new disk drive (like L:/ drive)?

---

### Post by sudodus on 2015-05-01
When you start installing, please select ***Something else*** at the partitioning window, to be able to select the partition you want to use for the root file system '/'.

But I suggest that we discuss what to do and how to do it before going ahead - and please remember to backup the current system.

---

### Post by Paneesh on 2015-05-01
Okay, I've got this EaseUS disk partition software to help extend that 16GB to 20 or even 25 gigs :) So no problem with that!
And I'll install in that partition!
And also, I'll stick on to Ubuntu because that's what my college people use and I'd try Xubuntu or even Edubuntu later!

Now the next step! How to install Ubuntu with the DVD that I have got.
I just uninstalled wubi!

---

### Post by Paneesh on 2015-05-01
I've backed up all my personal and important data to an external hard drive. :)

---

### Post by ajgreeny on 2015-05-01
> **Paneesh said:**
> And you've mentioned,
"If you have two disks, it is cleaner and easier to succeed to install Ubuntu to the other disk (not the one with Windows). In that case it is easier and less risky to disconnect the Windows disk while installing."

So what does it mean to have "two disks? :)
Is lt like partitioning a new disk drive (like L:/ drive)?
You only have one physical hard disk in your machine; Windows unfortunately confuses many people by naming partitions on the same hard disk as "Disk", when in reality they are not separate disks at all.

If you need to make changes to the exisiting Windows 7 partition sizes, I think it is always best done using Windows 7's own disk-management tool; don't bother with any third party tool to do that.

After shrinking Windows partitions always boot back into windows and let the system run chkdisk (maybe twice) to make sure it is still all OK.

---

### Post by Paneesh on 2015-05-01
DONE! :)
I just processed "chkdsk"!
And also, as you said, I've created a new partition from C drive and reserved 22 gigs of space.

And thanks for clarifying me with the terms "partitioning" and "disks"! Literally, they confused me since I downloaded Ubuntu and wanted to install it!

So what's the next step? :)

---

### Post by sudodus on 2015-05-01
1. Boot the computer from the DVD disk.

2. Follow the guided dialogue of the installer until you reach to the partitioning window.

3. Then you should select ***Something else*** which actually means manual partitioning.

So you can select the partition that you have prepared to be the root partition, in this case the partition with 22 GB. The root partition is symbolized with a slash character, '/'. I recommend to format it to the linux filesystem ***ext4***.

Usually the swap partition will be selected automatically.

At the bottom of the partitioning window there is a option to select where to install the bootloader. Check it, but with only one internal drive it should be pre-set correctly to the head of the internal drive, **/dev/sda** (there should be no partition digit).

4. And then I think it will be more straight-forward again (to follow the guided dialogue).

Good luck :-)

---

### Post by Paneesh on 2015-05-03
Thank you very much for your help!
I've successfully installed Ubuntu on my computer without wubi installer!
And I've committed some previous errors and as a consequence, I'm facing disk partition issues.
Like I used to get asked to select the OS in the boot menu and the first option was Windows 7 and then Ubuntu, but now, the system directly boots to Ubuntu boot menu, and if I don't select Windows within 10 seconds, I'll be logged into Ubuntu. 
I've messed up my disks while I installed, re-installed, partitioned disks, and deleting it for several times!

But I guess I'm gonna install both of the operating systems from the start one day when I find myself some free time!

Thanks for your help though! :)
Have a great day!

---

### Post by ajgreeny on 2015-05-03
It is quite normal for the first item in the grub menu to be the Linux OS in which grub is managed; if Windows 7 appeared first in the list previously that may be because you used wubi, which I have never seen in action and can not say what is normal, or it could be because you or someone else had reconfigured grub to boot to Windows first, which can be done very easily.

If both OSs will boot without error from choosing in grub I don't think you have made any errors with your partitions but have ended up with exactly what I would have expected.

---

### Post by sudodus on 2015-05-03
I'm glad it works for you now - even if things are not perfect :-)

If you think that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by Paneesh on 2015-05-04
Thank you for your help and being friendly throughout the process even though I was being like an noob :D
And for sure I'm going to mark this thread as "Solved" :)

---

### Post by Paneesh on 2015-05-04
Thank God! I was really worried that I had committed some mistake! And neither of the OS's return with an error message wile booting, so I'm good to work with them I guess!

Thanks for your support :)

---

### Post by sudodus on 2015-05-04
You are welcome :-)

---

