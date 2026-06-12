---
title: "How to Create EFI Partition"
date: 2018-11-16
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2018-11-16
I'm installing Ubuntu 16, 32bit on an old computer. How do I create the EFI / ESP partition?
I'm working of a USB Live Disk.
I can create the partions 
I have: 
/dev/sda
   freespace, this should be EFI, 750MB
   /dev/sda2, ext4, /, 76799MB
   /dev/sda3, ext4, /Home, 250GB
   swap, 2GB

In the Installation the partitioning tool doesn't seem to allow me to create the EFI partition. How do I do that?

---

### Post by ajgreeny on 2018-11-17
You say it is an old computer and you are using a 32 bit system in which case an EFI partition will not be or is very unlikely to be needed.

The EFI partition is required only if using GPT partitioning and having UEFI firmware instead of the older MBR/BIOS.

If for some reason you still wish to create a partition that you can use in future as EFI you can do so using gparted from a live system; make the partition approx 100MB, fat32.

See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for more info along with lots of tips at [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by webmanoffesto on 2018-11-17
Oh, that should have been obvious to me. Is there an alternative partion I need? Do I need a biosgrub partition?

---

### Post by oldfred on 2018-11-17
You can use the newer gpt partitioning with BIOS boot, but then need the bios_grub (1MB unformated with bios_grub flag).
If you are using the old MBR(msdos) partitioning, no extra partitions are required.

If using Windows, you have to use MBR for BIOS boot. 
And if newer system you have to use gpt partitioning for UEFI boot.
So if using Windows that often defines partitioning.

Back in 2010 I converted one drive to gpt for BIOS boot. I had XP on a different drive with MBR partitioning. So I know gpt works with many older BIOS. But that was a 64 bit install. System was part 2006 (cpu & drives) and part 2010 vintage(motherboard & video card).

What is your definition of older computer?
 We have seen some that say a 3 year old UEFI system is older and others with a 10 year old or older system.
Most systems will work with 64  bit install, even if older and originally had Windows 32 bit.

---

### Post by webmanoffesto on 2018-11-17
I guess I'm confused about the first partition, biosgrub?
That is set for 600 MB
In the Lubuntu Installer I can select that, click "edit", If I select "Format" then I can select the file system type, ext4, linuxswap, etc
and "Mount Point" such as /boot.

```
Error:
The installer failed to create partition on disk 'ATA WDC WD2500AVVS-6'.
========================================================================================== 
Create a new partition (2.06 GiB, linuxswap) on &#8216;/dev/sda&#8217; 
========================================================================================== 
========================================================================================== 
Job: Create new partition on device &#8216;/dev/sda&#8217; 
========================================================================================== 
Failed to add partition &#8216;New Partition&#8217; to device &#8216;/dev/sda&#8217;. Failed to add partition &#8216;New Partition&#8217; to device &#8216;/dev/sda&#8217;. 

```

This seemed promising
[[IMG]https://thumb.ibb.co/daMM9f/Lubutu-Installation-n03-v01.jpg[/IMG]]("https://ibb.co/daMM9f")

What's the correct "install boot loader on" should I set it to "Boot Partition (/boot). That would make sense. But still "next" is greyed out.

Hewlett Packard Pentium
1GB RAM?
CPU Intel Pentium 4 ... 2.66GHz

```

$ lshw
lubuntu                     
    description: Low Profile Desktop Computer
    product: HP d530 SFF(DJ751S)
    vendor: Hewlett-Packard
    serial: USU34808J7
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=low-profile cpus=1 uuid=2A872090-6920-D811-BBD8-9DDAD550000D
  *-core
       description: Motherboard
       product: 085Ch
       vendor: Hewlett-Packard
       physical id: 0
       serial: USU34808J7
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 1
          version: 786B2 v1.11
          date: 07/10/2003
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.2.9
          slot: XU1 PROCESSOR
          size: 2666MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cpuid cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: Internal L1 Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: burst internal write-back data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: Cache L2
             size: 512KiB
             capacity: 4MiB
             capabilities: burst internal write-back data
             configuration: level=2
     *-memory:0
          description: System Memory
          physical id: 27
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: M3 68L3223FTN-CB3
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 0
             serial: 62630F41
             slot: DIMM1
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: NT256D64S88B1G-6K
             vendor: JEDEC ID:7F 7F 7F 0B 00 00 00 00
             physical id: 1
             serial: 00000000
             slot: DIMM2
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: NT256D64S88B1G-6K
             vendor: JEDEC ID:7F 7F 7F 0B 00 00 00 00
             physical id: 2
             serial: 00000000
             slot: DIMM3
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: NT256D64S88B1G-6K
             vendor: JEDEC ID:7F 7F 7F 0B 00 00 00 00
             physical id: 3
             serial: 00000000
             slot: DIMM4
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 28
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 512KiB
             width: 4 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f8000000-fbffffff
        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f7ffffff memory:fc400000-fc47ffff ioport:14e0(size=8) memory:c0000-dffff
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:40100000-40100fff
        *-usb:0
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1440(size=32)
        *-usb:1
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1460(size=32)
        *-usb:2
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1480(size=32)
        *-usb:3
             description: USB controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fc480000-fc4803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: memory:fc500000-fc7fffff
           *-network:0
                description: Ethernet interface
                product: NetXtreme BCM5782 Gigabit Ethernet
                vendor: Broadcom Inc. and subsidiaries
                physical id: 2
                bus info: pci@0000:05:02.0
                logical name: enp5s2
                version: 03
                serial: 00:0d:9d:da:d5:50
                capacity: 1Gbit/s
                width: 64 bits
                clock: 66MHz
                capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5782-v3.13 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
                resources: irq:20 memory:fc500000-fc50ffff
           *-network:1
                description: Wireless interface
                product: RT2561/RT61 802.11g PCI
                vendor: Ralink corp.
                physical id: 9
                bus info: pci@0000:05:09.0
                logical name: wlp5s9
                version: 00
                serial: 00:21:29:e0:4a:87
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt61pci driverversion=4.18.0-10-generic firmware=0.8 ip=192.168.1.167 latency=66 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:18 memory:fc510000-fc517fff
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide isa_compatibility_mode_controller__supports_both_channels_switched_to_pci_native_mode__supports_bus_mastering bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:14c0(size=16) memory:40101000-401013ff
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pci_native_mode_controller__supports_both_channels_switched_to_isa_compatibility_mode__supports_bus_mastering bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:14f8(size=8) ioport:1810(size=4) ioport:1800(size=8) ioport:1814(size=4) ioport:14d0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:fc00(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:1000(size=256) ioport:1400(size=64) memory:fc480400-fc4805ff memory:fc480600-fc4806ff
     *-scsi:0
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: SCSI CD-ROM
             product: CD-ROM SC-148C
             vendor: SAMSUNG
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: B100
             capabilities: removable audio
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 4
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD2500AVVS-6
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sda
             version: 3A01
             serial: WD-WCAV19248855
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=0004d641
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: 4245e25a-35f5-45aa-98ee-c1bcd1ab56ca
                size: 600MiB
                capacity: 600MiB
                capabilities: primary bootable boot journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2018-11-16 15:32:05 filesystem=ext4 lastmountpoint=/tmp/calamares-root-vyxumbyh/boot modified=2018-11-17 11:57:01 mounted=2018-11-17 11:57:01 state=clean
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sda2
                version: 1.0
                serial: b8ec170e-50c1-4322-ba0d-229ec3d21b2a
                size: 1012MiB
                capacity: 1012MiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2018-11-16 15:31:57 filesystem=ext4 lastmountpoint=/tmp/Calamares-GnmmFw modified=2018-11-17 12:04:50 mounted=2018-11-17 12:04:50 state=clean
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@3:0.0.0,3
                logical name: /dev/sda3
                version: 1.0
                serial: 2bdcfe58-be61-4119-ba8d-0fb375eab829
                size: 231GiB
                capacity: 231GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2018-11-16 22:50:10 filesystem=ext4 modified=2018-11-17 11:57:02 mounted=2018-11-17 11:57:02 state=clean
     *-scsi:2
          physical id: 6
          bus info: usb@1:5
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Cruzer
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 1.10
             size: 29GiB (32GB)
             capabilities: removable
             configuration: ansiversion=2 logicalsectorsize=512 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 29GiB (32GB)
                capabilities: partitioned partitioned:dos
                configuration: signature=686a6515
              *-volume:0
                   description: Windows FAT volume
                   vendor: SYSLINUX
                   physical id: 1
                   logical name: /dev/sdb1
                   logical name: /isodevice
                   version: FAT32
                   serial: 7f5d-e59c
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat label=MULTISYSTEM mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   logical name: /dev/sdb2
                   logical name: /media/lubuntu/Tom
                   version: 1.0
                   serial: eb47bc29-aa23-4b83-a52e-543930de014c
                   size: 1023MiB
                   capacity: 1023MiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2018-11-16 13:10:05 filesystem=ext4 label=Tom modified=2018-11-17 11:57:52 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime mounted=2018-11-17 11:57:52 state=mounted

```

---

### Post by oldfred on 2018-11-17
You always install boot loaders to the drive like sda, not to a partition like sda1.
Computers boot from UEFI/BIOS.
With BIOS it jumps to the MBR or first sector of hard drive for more boot code. That is tiny so code in MBR loads additional boot code from other locations. Each operating system & its boot loader is different.
With UEFI, it looks for an ESP - efi system partition which is FAT32 with boot flag.

If using gpt and BIOS, you need a 1 or 2MB unformatted partition with bios_grub flag.
But if UEFI, the ESP is FAT32 and anywhere from 100 to 600MB.

Swap is also unformatted. So if you selected ext4 & swap it should give an error. Never seen that.
But you do not need swap partition with 18.04 as it uses swap file.

Are you installing Ubuntu or one of the lightweight flavors?
With only 1GB of RAM, a lightweight version will work, where full Ubuntu may not.
       Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

### Post by webmanoffesto on 2018-11-17
The below seemed promising, but then I got 
[FONT=courier new]Installation Failed: Failed to unpack image /cdrom/casper/filesystem.squashfs[/FONT]
[FONT=courier new]rsync failed with error code 11.[/FONT]

> **oldfred said:**
> 
You always install boot loaders to the drive like sda, not to a partition like sda1.

Okay, I have it set to "Install boot loader on /dev/sda".

[[IMG]https://thumb.ibb.co/fuQy5L/Lubutu-Installation-n04-v01.jpg[/IMG]]("https://ibb.co/fuQy5L")

[[IMG]https://thumb.ibb.co/fYCpC0/Lubutu-Installation-n05-v01.jpg[/IMG]]("https://ibb.co/fYCpC0")

SDA1: 8MB, Partition Type: Primary, File System: unformatted, Flags: biod-grub 
SDA2: 590MB, Primary, ext4, Mount Point: /, Flags: root
SDA3: 230GB, ext4, Mount Point /home, Flags: none
SDA4: 1012MB, Primary, Filesystem: linuxswap, MountPoint: greyed out, Flags: swap
Install Boot Loader on /dev/sda

I'm trying to install Lubuntu 18.10. I hope this is the 32bit version, that's what I intended to do. When I run 
$ uname -srm 
> Linux 4.18.0-10-generic i686

Regarding the boot partition. I can "edit" /dev/sda1. If I select to format it, in "edit exisiting partition" then in "File System" I select "unformatted" I can select "Flag: bios-grub"

More specifics on this Pentium
```

lubuntu@lubuntu:~$ uname -srm
Linux 4.18.0-10-generic i686
lubuntu@lubuntu:~$ uname -r
4.18.0-10-generic
lubuntu@lubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            476M     0  476M   0% /dev
tmpfs            99M  1.1M   98M   2% /run
/dev/sdb1        29G  8.9G   20G  31% /isodevice
/dev/loop0      1.6G  1.6G     0 100% /cdrom
/dev/loop1      1.6G  1.6G     0 100% /rofs
/cow            495M   70M  426M  14% /
tmpfs           495M   35M  461M   7% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           495M     0  495M   0% /sys/fs/cgroup
tmpfs           495M  516K  495M   1% /tmp
tmpfs            99M  8.0K   99M   1% /run/user/999
/dev/sdb2       991M  1.3M  923M   1% /media/lubuntu/Tom
/dev/sda2       567M  555M     0 100% /tmp/calamares-root-zs7bnx3t
/dev/sda3       227G   61M  216G   1% /tmp/calamares-root-zs7bnx3t/home
tmpfs           495M     0  495M   0% /tmp/calamares-root-zs7bnx3t/run
lubuntu@lubuntu:~$ ls /boot
abi-4.18.0-10-generic     memtest86+.elf
config-4.18.0-10-generic  memtest86+_multiboot.bin
grub                      retpoline-4.18.0-10-generic
memtest86+.bin            System.map-4.18.0-10-generic
lubuntu@lubuntu:~$ dpkg -l | grep linux
ii  binutils-i686-linux-gnu                      2.31.1-6ubuntu1                            i386         GNU binary utilities, for i686-linux-gnu target
ii  console-setup-linux                          1.178ubuntu9                               all          Linux specific part of console-setup
ii  libselinux1:i386                             2.8-1build1                                i386         SELinux runtime shared libraries
ii  libv4l-0:i386                                1.14.2-1                                   i386         Collection of video4linux support libraries
ii  libv4lconvert0:i386                          1.14.2-1                                   i386         Video4linux frame format conversion library
ii  linux-base                                   4.5ubuntu1                                 all          Linux image base package
ii  linux-firmware                               1.175                                      all          Firmware for Linux kernel drivers
ii  linux-generic                                4.18.0.10.11                               i386         Complete Generic Linux kernel and headers
ii  linux-headers-4.18.0-10                      4.18.0-10.11                               all          Header files related to Linux kernel version 4.18.0
ii  linux-headers-4.18.0-10-generic              4.18.0-10.11                               i386         Linux kernel headers for version 4.18.0 on 32 bit x86 SMP
ii  linux-headers-generic                        4.18.0.10.11                               i386         Generic Linux kernel headers
ii  linux-image-4.18.0-10-generic                4.18.0-10.11                               i386         Linux kernel image for version 4.18.0 on 32 bit x86 SMP
ii  linux-image-generic                          4.18.0.10.11                               i386         Generic Linux kernel image
ii  linux-libc-dev:i386                          4.18.0-10.11                               i386         Linux Kernel Headers for development
ii  linux-modules-4.18.0-10-generic              4.18.0-10.11                               i386         Linux kernel extra modules for version 4.18.0 on 32 bit x86 SMP
ii  linux-modules-extra-4.18.0-10-generic        4.18.0-10.11                               i386         Linux kernel extra modules for version 4.18.0 on 32 bit x86 SMP
ii  linux-sound-base                             1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  pptp-linux                                   1.9.0+ds-2                                 i386         Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                     3:6.04~git20171011.af7e95c3+dfsg1-4ubuntu1 i386         collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                              3:6.04~git20171011.af7e95c3+dfsg1-4ubuntu1 all          collection of bootloaders (common)
ii  syslinux-legacy                              2:3.63+dfsg-2ubuntu9                       i386         Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                   2.32-0.1ubuntu2                            i386         miscellaneous system utilities
lubuntu@lubuntu:~$ 

```

---

### Post by webmanoffesto on 2018-11-17
Ubuntu Mate 18 pointed out that the root partition has to be at least 6GB. That makes sense. Trying that now.

New Error Messages

A) Partition(s) 4 on /dev/sda have been written, buit we have been unable to inform the kernel of the change, probably because it/they are in use. As a result, the old partition(s) will remain in use. You should reboot now before making further changes.
- Is that because I'm running off a Flash drive?

and

B) The creation of a swap space in partition #4 of SCSI4 (0,0,0) (sda) failed.

---

### Post by oldfred on 2018-11-17
I always create / at 25 to 30GB, but only use a small part of it. But that gives plenty of room for just about any standard programs. Games would perhaps take more space, but I do not believe they have to be in /.

```
fred@Bionic-Z170N:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  2.0M  1.6G   1% /run
/dev/sda4        25G  7.8G   16G  33% /

```

---

### Post by Dennis N on 2018-11-17
> Partition(s) 4 on /dev/sda have been written...
You may have pressed "Install", and then it's too late to make further changes, so your root partition was made 592 mB, and the installer fails since it can't fit you root files and folders in there. It's important to check details carefully before committing to Install. Best option now is to redo your partition setup.

---

