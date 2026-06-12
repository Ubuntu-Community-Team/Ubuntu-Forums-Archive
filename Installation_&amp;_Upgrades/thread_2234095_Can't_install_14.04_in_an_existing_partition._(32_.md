---
title: "Can't install 14.04 in an existing partition. (32 bit)"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by lift_test on 2014-07-12
I've always used the alternate install previously and had very little trouble but this time if I try to use an existing partition it will not install.  It seems quite happy to start wiping everything and installing but the "partitioner"? will not do anything. If I double click on the partition I want to install on it shows it in the window but disappears as soon as the cursor goes over it. Any ideas?

---

### Post by slooksterpsv on 2014-07-12
You can check the output of dmesg by switching to a TTY via ALT+F2

Are you using the alternate still or the regular?

There could be an issue with the partition itself.

---

### Post by lift_test on 2014-07-12
> **slooksterpsv said:**
> You can check the output of dmesg by switching to a TTY via ALT+F2

Are you using the alternate still or the regular?

There could be an issue with the partition itself.

There is no alternate for 14.04 and yes could be problem with partition but it won't actually move from highlighting the first partition on either drive.

---

### Post by Bucky Ball on 2014-07-12
Can you delete the partition then set the partitioner to create an EXT4 partition and install / or whatever you are wanting to put there to the free space?

---

### Post by lift_test on 2014-07-12
> **Bucky Ball said:**
> Can you right click and delete the partition then repartition the free space and try again?
No It seems to be frozen, it won't do anything.  The only thing I can make it do is change from one disk to the other.

---

### Post by Bucky Ball on 2014-07-12
This is a 32bit machine? Shouldn't make much difference, but have you tried the 64bit if it isn't? Make better use of your hardware, depending on what you have. What are the specs of the machine?

---

### Post by lift_test on 2014-07-12
Thanks for all the replies, got fed up with it and just let it wipe everything, bad move, will have to find the 12.04 disk. the computer is running slower than treacle.

---

### Post by Bucky Ball on 2014-07-12
What are the machine specs???

---

### Post by lift_test on 2014-07-12
I always build my own machines, this one is the oldest it has an Asus P4S8X motherboard.

---

### Post by Bucky Ball on 2014-07-12
Bit more than that, please. CPU and amount of RAM.

---

### Post by lift_test on 2014-07-13
Sorry can't remember, can you find out from within ubuntu?  Found lshw, results below

```
old-faithful              
    description: Tower Computer
    product: System Name
    vendor: System Manufacturer
    version: System Version
    serial: SYS-1234567890
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=tower
  *-core
       description: Motherboard
       product: P4S8X
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: xxxxxxxxxxx
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: ASUS P4S8X ACPI BIOS Revision 1005
          date: 10/23/2003
          size: 64KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.4
          slot: PGA 478
          size: 2GHz
          capacity: 3200MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 8KiB
             capacity: 32KiB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: pipeline-burst synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 512MiB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: DIMM 3
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 645xx
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:e8000000-ebffffff
        *-pci
             description: PCI bridge
             product: AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: memory:e7000000-e7ffffff memory:eff00000-febfffff
           *-display
                description: VGA compatible controller
                product: NV28 [GeForce4 Ti 4200 AGP 8x]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
                resources: irq:16 memory:e7000000-e7ffffff memory:f0000000-f7ffffff memory:effe0000-efffffff
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO] LPC Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
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
             resources: irq:0 ioport:e600(size=32)
        *-firewire
             description: FireWire (IEEE 1394)
             product: FireWire Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list rom
             configuration: driver=firewire_ohci latency=64 maxlatency=12 mingnt=4
             resources: irq:17 memory:e6800000-e6800fff memory:efee0000-efefffff
        *-ide
             description: IDE interface
             product: 5513 IDE Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:b400(size=16)
        *-multimedia:0
             description: Multimedia audio controller
             product: SiS7012 AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=32 maxlatency=11 mingnt=52
             resources: irq:18 ioport:a400(size=256) ioport:a000(size=128)
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
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:9 memory:e6000000-e6000fff
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
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:21 memory:e5800000-e5800fff
        *-usb:2
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:22 memory:e5000000-e5000fff
        *-usb:3
             description: USB controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:23 memory:e4800000-e4800fff
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:e0:18:a5:45:a4
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.66 latency=32 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100Mbit/s
             resources: irq:19 ioport:9800(size=256) memory:e4000000-e4000fff memory:efec0000-efedffff
        *-multimedia:1
             description: Multimedia video controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder
             vendor: Conexant Systems, Inc.
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: vpd pm bus_master cap_list
             configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20
             resources: irq:17 memory:e3000000-e3ffffff
        *-storage
             description: RAID bus controller
             product: PDC20376 (FastTrak 376)
             vendor: Promise Technology, Inc.
             physical id: e
             bus info: pci@0000:00:0e.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list
             configuration: driver=sata_promise latency=96 maxlatency=18 mingnt=4
             resources: irq:16 ioport:9400(size=64) ioport:9000(size=16) ioport:8800(size=128) memory:e2800000-e2800fff memory:e2000000-e201ffff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: MAXTOR STM332082
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 9QF6RLCT
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0007a266
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 1baf6c0d-3520-4ad7-8ee9-0efa703b514d
                size: 296GiB
                capacity: 296GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-07-12 21:56:07 filesystem=ext4 lastmountpoint=/ modified=2014-07-12 22:46:43 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-07-13 13:58:40 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1535MiB
                capacity: 1535MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1535MiB
                   capabilities: nofs
        *-disk:1
             description: ATA Disk
             product: SAMSUNG SP0842N
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sdb
             version: BH10
             serial: S0DWJ1DP150477
             size: 31GiB (33GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000eab42
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sdb1
                version: 1.0
                serial: ab665ca0-2d02-4477-a8f0-0ae6c690f2eb
                size: 29GiB
                capacity: 29GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-10-23 18:20:34 filesystem=ext4 lastmountpoint=/ modified=2014-07-12 21:34:23 mounted=2014-07-12 21:34:23 state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.1.0,2
                logical name: /dev/sdb2
                size: 1534MiB
                capacity: 1534MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 1534MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM GH22NP20
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 2.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

---

### Post by oldfred on 2014-07-14
Please use code tags, or # in advanced editor.

You have a Pentium 4 with 1.5GB of RAM and an older nVidia card.

You probably now cannot run full Unity as old nVidia just may not have enough horsepower to run it. My old laptop is also 1.5GB of RAM with just the Intel chip. I do install full Ubuntu but Unity just is so slow as to be unusable, so I install gnome-panel also known as fallback or flashback.

I have nVidia card on my desktop and have to use nomodeset to boot installer and first boot after install or until I install proprietary nVidia driver. Your will need a legacy nVidia driver.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

      
 nVidia versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

Looks like this driver is correct for you:
96.43.xx

---

### Post by lift_test on 2014-07-19
My apologies for not responding sooner, have been away for the week.  Will try your suggestions as soon as I've found out why the wired network is disconnected, suspect card is at fault, all other machines are connecting OK.  Curious about using code tags, I can understand why if it is code but that was just a list, no commands involved?

---

### Post by deathkarr on 2014-07-19
When I've done installs similar to this on older machines, I've always found that if you want to use the latest version of ubuntu then you should use a lighter Ui, lxde or something similar to that.

---

### Post by slooksterpsv on 2014-07-19
> **lift_test said:**
> My apologies for not responding sooner, have been away for the week.  Will try your suggestions as soon as I've found out why the wired network is disconnected, suspect card is at fault, all other machines are connecting OK.  Curious about using code tags, I can understand why if it is code but that was just a list, no commands involved?

The code tags are just for the forum
```

I can type code in here and it appears in a box, and if it gets too long it gives you scroll bars so what you paste isn't taking up the entire page essentialy.

```

There's also, less used PHP tags
[php]
#include <iostream>
//I believe this only syntax highlights code
/*for easier readability */
int main(int argc, char* argv[])
{
return 0;
}
[/php]

The HTML Tag, no clue:
[HTML]
//syntax?
<?php
phpinfo() 
?>
[/HTML]

Guess different format for highlighting for PHP and HTML tags.

---

### Post by lift_test on 2014-07-20
I understand about the tags now, thank you.  However I think I will be needing a new Ubuntu machine, it denies all knowledge of the LAN (although the LED is flashing) and shows a reluctance to boot.  Thank you all for your help.

---

### Post by Bucky Ball on 2014-07-20
Please post a new thread regarding the wireless. It might not be as hopeless as you think. Include the output of this command in the new thread:

```
sudo lshw -C network
```

... to get things started. Good luck.

---

### Post by lift_test on 2014-07-20
> **Bucky Ball said:**
> Please post a new thread regarding the wireless. It might not be as hopeless as you think. Include the output of this command in the new thread:

```
sudo lshw -C network
```

... to get things started. Good luck.
Thanks for the offer but the machine now hangs when booting, in mind of it's age I think it should RIP.;)

---

### Post by Bucky Ball on 2014-07-21
> **lift_test said:**
> Thanks for the offer but the machine now hangs when booting, in mind of it's age I think it should RIP.;)

Hehe. A pity, but perhaps you're right. ;(

---

