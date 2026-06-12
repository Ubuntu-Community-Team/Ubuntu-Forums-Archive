---
title: "cannot find hard drive during install; can find drive when booted from liveCD"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by nogoodnamesleft on 2011-01-21
This Ubuntu 10.10

If I run Ubuntu from a liveCD, it boots up, it can see the hard drive and it can see, and read to and write from, from the hard disk.

If i run the ubuntu installer, it cannot see the hard drive at all. It's  not a case not seeing any partitions, it's a case of not seeing the drive. It won't even list the drive.

The machine has a SATA controller connected to an 80 GB hard drive, that contains a 35 gig window partition and about 35-ish gigs of unpartitioned space. I run Ubuntu from a USB stick.

The liveCD, once booted, shows /dev/sda and /dev/sdb - the usbstick and the hard drive repsectively. The partitioning tools e.g. gparted work. I can create/delete partitions in the freespace and I can read/write to the NTFS windows partition.

The installer lists only one hard drive, the USB stick. It won't list the internal HDD.

I don't know linux at all

I think it's either missing a driver/config setting in the installer or the partitions on the hard drive are "donald ducked" in such a way that causes ubuntu to refuse to recognise that there is a hard drive present.

---

### Post by nogoodnamesleft on 2011-01-21
Partition info follows for the drive (from WPE). 35ish gig NTFS, 36ish freespace, not dynamic and not overlapping.

Disk 1, Total Sectors: 156301488, 
Name: ST380811AS, 
GUID Partition Table: NO, 
Dynamic Disk: NO, 
CHS:9729/255/63

letter: C 
PartID:  7 
Start:          63 
End:    74589794 
Size:    74589732 
FsId:  7 
Label:               Data01 
ClusterSize:   8 
FreeSectors:    57001240 
Primary: 1 
Bootable: 1 
BootVolume: 1 
SystemVolume: 1

letter: * 
PartID:  0 
Start:    74589795 
End:   156301487 
Size:    81711693 
FsId:  0 
Label: 
                     ClusterSize:   1 
FreeSectors:    81711693 
Primary: 0 
Bootable: 0 
BootVolume: 0 
SystemVolume: 0

---

### Post by nogoodnamesleft on 2011-01-21
An update of my current progress.  I have tried the options on the Ubuntu LiveCD bootup to turn off APIC etc, with no luck.  I've tried the alternative CD. The text mode menus brought back happy memories of DOS adventure games, however still no luck. I didn't understand some of the options but I tried a lot of combinations. The partitioning tool there doesn't see the hard drive.  I really have no idea.  It's a very old motherboard, an Abit SD-80, if that helps. It's a SiS661FX chipset. I know it's junk but it still works, and it's a good proxy and fileserver.

---

