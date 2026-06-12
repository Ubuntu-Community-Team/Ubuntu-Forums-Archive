---
title: "Ubuntu does not find my hard disks (it looks like)"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by Ole22 on 2011-09-23
Hello!

I tried to install Ubuntu on my new computer with windows 7. I first tried wubi but when I tried to boot it, it said it could not find some kind of iso file. 

I then tried to install ubuntu from both a usb and then a cd. The problem seems to be that it does not recognize my hard drive. When i tried to install from a cd it said it was not enough space. When i tried to install it from usb i came longer in the installation prosses but it could not recognize any other devices other than the usb. It seemed not to be able to find my hard disks. 

It is the first time I try to install another operating system. Does anyone know what to do?

---

### Post by psrdotcom on 2011-09-23
How many partitions do you have?

If it is more than 3, then in windows 7 it will automatically consider those drives as logical volumes. And in Logical volumes, we can't install any OS.

To install the OS, the drive should be primary partition if I am correct.

---

### Post by Rubi1200 on 2011-09-23
> **Ole22 said:**
> Hello!

I tried to install Ubuntu on my new computer with windows 7. I first tried wubi but when I tried to boot it, it said it could not find some kind of iso file. 

I then tried to install ubuntu from both a usb and then a cd. The problem seems to be that it does not recognize my hard drive. When i tried to install from a cd it said it was not enough space. When i tried to install it from usb i came longer in the installation prosses but it could not recognize any other devices other than the usb. It seemed not to be able to find my hard disks. 

It is the first time I try to install another operating system. Does anyone know what to do?
Hi and welcome to the forums :)

Please post the following information so we can help you troubleshoot this issue.

1. full specifications for the computer, especially RAM and graphics card

2. the results of the boot info script (there is a link at the bottom of my post with instructions)

3. a screenshot of the Windows Disk Management utility showing the drives on the computer

Thanks.

---

### Post by Ole22 on 2011-09-23
> **Rubi1200 said:**
> Hi and welcome to the forums :)

Please post the following information so we can help you troubleshoot this issue.

1. full specifications for the computer, especially RAM and graphics card

2. the results of the boot info script (there is a link at the bottom of my post with instructions)

3. a screenshot of the Windows Disk Management utility showing the drives on the computer

Thanks.

Hi! :)

I tried to copy from another list to find out what is in my computer 


1.
"Corsair TX V2 650W PSU
ATX 12V V2.3, 80 Plus Bronze, Standard. 2x 6+2-pin
PCIe, 8x SATA, 140mm Vifte

Intel® Core# i7-2600K Processor
Socket-LGA1155, Quad Core, 3.4Ghz, 8MB, 95W,
Boxed w/fan

Gigabyte GA-Z68X-UD4, Socket-1155
ATX, Z68, DDR3, 2xPCIe(2.0)x16, CFX& SLI, FW,
SATA 6Gb/s,USB 3.0, Dolby,16 phase

Kingston DDR3 HyperX 1600MHz 16GB
Kit w/4X HyperX 4GB DDR3, CL9-9-9-27, 240pin

XFX Radeon HD 6950 1GB GDDR5 "Dual Fan"
PCI-Express 2.1, 2xDVI, HDMI, 2xmini-DisplayPort,
800MHz

Corsair SSD Force Series# F115, 115GB
SATA2, 2,5", 285MB/275MB/s read/write, incl 2,5" to
3,5" bracket

OEM SSD 2.5" to 3.5" Bracket SATA
SSD 2.5" to 3.5" (Bracket and screws)

Western Digital Caviar® Black 2TB
SATA 6Gb/s (SATA 3.0), 64MB Cache, 7200RPM, 3,5",
Dual processor


MS COA Label Windows Home Premium 7
Nordic, 32/64 bit
MS DVD Win H.P/Pro/Ultimate 7 NO 64bit"



2.                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 
sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:   Syslinux looks at sector 61772 of /dev/sda1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================
 
Drive: sda _____________________________________________________________________

Disk /dev/sda: 8127 MB, 8127512576 bytes
5 heads, 32 sectors/track, 99212 cylinders, total 15874048 sectors
Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          8,064    15,874,047    15,865,984   c W95 FAT32 (LBA)

 
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        13F0-2576                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options
 
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
 

========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
 prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sda1: Location of files loaded by Syslinux: ==================

            GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
             ?? = ??             syslinux/vesamenu.c32                          1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)
 
========= Devices which don't seem to have a corresponding hard drive: =========

no block devices found 


3. maybe this is screen shot of what you meant :)

---

### Post by oldfred on 2011-09-23
Nice System:)

But boot script did not see drives either, which is unusual. Does BIOS show your drives?

You have a new system with UEFI and a BIOS mode. Your Windows could be installed with the old BIOS mode and MBR partitions or newer UEFI mode and gpt partitions. Boot script does not fully parse efi boot partitions, but would show the gpt drive(s) if you were in that mode.

[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

