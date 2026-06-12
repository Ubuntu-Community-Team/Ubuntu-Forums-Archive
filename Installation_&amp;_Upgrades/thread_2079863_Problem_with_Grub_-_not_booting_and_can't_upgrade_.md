---
title: "Problem with Grub - not booting and can't upgrade grub"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by vocoder42 on 2012-11-02
When I reboot my machine, it always says something like OS not found. If I boot from a livecd and select 'boot from first disk' it will boot into ubuntu without issue.

after a recent apt-get upgrade, grub was updated but it comes back with the error:

warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
error: will not proceed with blocklists.

how can I fix this?  here is part of my bootscript file:

```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
    the same hard drive for core.img. core.img is at this location and looks
    for (,msdos1)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of
                       sda1 and looks at sector 78954 of the same hard drive
                       for core.img, but core.img can not be found at this
                       location.
    Operating System:
    Boot files:        /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sda5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:

dev-root': _____________________________________________________________________

    File system:
    Boot sector type:  Unknown
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''

dev-swap_1': ___________________________________________________________________

    File system:
    Boot sector type:  Unknown
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1200.3 GB, 1200264314880 bytes
64 heads, 32 sectors/track, 1144661 cylinders, total 2344266240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             501,758 2,344,265,727 2,343,763,970   5 Extended
/dev/sda5             501,760 2,344,265,727 2,343,763,968  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/dev-root 4aee45a5-befc-437d-ae5f-7153b7b95c19   ext4
/dev/mapper/dev-swap_1 62c7010d-d69b-4448-9abb-1160435b5181   swap
/dev/sda1        b16fe7a4-0d99-4df9-978c-f117c6981624   ext2
/dev/sda5        ImPJQS-3i1J-MvCe-M0XQ-Rgpa-KWgO-rE5y7j LVM2_member
/dev/sr0                                                iso9660    Ubuntu-Server 10.04.1 LTS i386

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
dev-root
dev-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/dev-root /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /boot                    ext2       (rw)


============================= sda1/grub/grub.cfg: ==============================


```

---

