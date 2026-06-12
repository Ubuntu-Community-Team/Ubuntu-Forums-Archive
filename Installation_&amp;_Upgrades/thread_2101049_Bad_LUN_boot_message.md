---
title: "Bad LUN boot message"
date: 2013-01-03
forum: Installation &amp; Upgrades
---

### Post by Rob Sayer on 2013-01-03
So I'm getting the BadLUN message (and bad target ones as well) on boot.  Linux and windows 7.  It seems to work OK now, but it's disconcerting.  Since I don't know what exactly it does mean I can't say if it will continue to work.

It's actually 32 bit ubuntu 12.04 based mint 13/maya but I'm exclusively using xfce 4.8 installed with synaptic.  The Mint implementation of xfce *stinks*.  It's debian based, not ubuntu (and I wanted ubuntu base .... I want consistency), slow, and just plain flaky.

I'd be using xubuntu (like on my other 2 computers) except it's a Cedarview Atom cpu with the infamous 3600 graphics.  When I tried to load the drivers under the xfce "additional drivers" in setup it bricked the video.  Not impressed.  And the process for fixing it looks very convoluted.

However, I read about someone who installed mint 13 and just used synaptic to load the cedarview drivers and it worked.  It was worth a shot to me, and it did work.

The kernel version is 3.2.0-23-generic.  I think that's what shipped with mate 13, if not maybe an older one.  That may have been why the cedarview drivers worked as well as they did and so simply.  I never tried that with xubuntu.

Anyway, the package manager said it was holding that kernel version, and if this bad LUN message turns out to be kernel related I'll still stick to that kernel.  I kind of want the video to work reasonably well, even though it's just a netbook.

While I'm not really sure what's happening here, here's the results from what I've gleaned elsewhere.

This is from sudo fdisk -l ...

> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x421224e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   27  Hidden NTFS WinRE
/dev/sda2   *    27265024    27469823      102400    7  HPFS/NTFS/exFAT
/dev/sda3        27469824   234291862   103411019+   7  HPFS/NTFS/exFAT
/dev/sda4       234293246   625141759   195424257    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       234293248   623069183   194387968   83  Linux
/dev/sda6       623071232   625141759     1035264   82  Linux swap / Solaris

Disk /dev/sdc: 4000 MB, 4000317440 bytes
114 heads, 49 sectors/track, 1398 cylinders, total 7813120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          16     7813119     3906552    b  W95 FAT32

This, from cat /proc/scsi/scsi ...

> Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD3200BPVT-2 Rev: 01.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: Generic- Model: xD/SD/M.S.       Rev: 1.00
  Type:   Direct-Access                    ANSI  SCSI revision: 02

This from cat  /etc/fstab

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d7422fe2-6f1f-4499-bdfa-eb74de12df8b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7690c15e-3c46-41de-ae3e-2cf4ecc6b3f1 none            swap    sw              0       0

I don't know if there is any conflict with the SD card.  Never used one of those slots once.

Note the message from sudo fdisk -l ...  "Extended Partition 4 does not start on physical sector boundary.".  Seems important, eh?

Do I need to reinstall?  Again?  I've never had so many problems with ubuntu or xubuntu installs.  It's actually seeming to work fine now after installing xfce 4.8 myself.

---

### Post by Rob Sayer on 2013-01-04
I searched the following:

linux kernel bug "3.2.0-23-generic" lun

All I got was network problems and problems with RAID drive setups.  I've had no network problems and, while it seems closer to what's going on, I've never tried to set up RAID drives.

---

### Post by Rob Sayer on 2013-01-04
Here's my PCI devices:

> $ lspci
00:00.0 Host bridge: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

---

