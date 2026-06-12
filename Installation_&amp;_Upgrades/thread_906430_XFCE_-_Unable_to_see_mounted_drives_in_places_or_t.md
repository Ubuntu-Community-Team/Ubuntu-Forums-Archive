---
title: "XFCE - Unable to see mounted drives in places or thunar"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by lilpaul on 2008-08-31
Im new to linux, so please be gentle.

I have just installed the latest Linux Mint 5 XFCE version - which i believe is based on the hardy heron, and upon completion I noticed my hard drives where not mounted on startup. I have performed the following actions so far:-

-- Identify Partitions Available
Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e129e12

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4310 34620043+ 83 Linux
/dev/sda2 4311 4500 1526175 5 Extended
/dev/sda5 4311 4500 1526143+ 82 Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3bb47bdf

Device Boot Start End Blocks Id System
/dev/sdb1 1 19582 157292383+ 7 HPFS/NTFS
/dev/sdb2 19583 38913 155276257+ f W95 Ext'd (LBA)
/dev/sdb5 19583 38913 155276226 b W95 FAT32

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfcd2fcd2

Device Boot Start End Blocks Id System
/dev/sdc1 1 6527 52428096 7 HPFS/NTFS
/dev/sdc2 6528 38913 260140545 f W95 Ext'd (LBA)
/dev/sdc5 6528 38913 260140513+ 7 HPFS/NTFS

-- Identify UUID of partitons to be added into fstab
lilpaul@smiley1 ~ $ sudo blkid /dev/sdb1
/dev/sdb1: UUID="5276E19976E17DDB" LABEL="MOVIES" TYPE="ntfs"
lilpaul@smiley1 ~ $ sudo blkid /dev/sdb5
/dev/sdb5: LABEL="MUSIC" UUID="8B75-22B6" TYPE="vfat"
lilpaul@smiley1 ~ $ sudo blkid /dev/sdc1
/dev/sdc1: UUID="041A84721A846312" LABEL="APPS" TYPE="ntfs"
lilpaul@smiley1 ~ $ sudo blkid /dev/sdc5
/dev/sdc5: UUID="BEDC96B5DC966803" LABEL="DOWNLOADS" TYPE="ntfs"

-- backup fstab
sudo cp /etc/fstab /etc/fstab_310808

-- make file system mount point names
sudo mkdir /media/apps
sudo mkdir /media/downloads
sudo mkdir /media/movies
sudo mkdir /media/music

-- add mountpoints into fstab
sudo vi /etc/fstab

# /dev/sdb1
UUID="5276E19976E17DDB" /media/movies ntfs defaults,umask=007,gid=46,noatime 0 0
# /dev/sdb5
UUID="8B75-22B6" /media/music vfat defaults,umask=007,gid=46,noatime 0 0
# /dev/sdc1
UUID="041A84721A846312" /media/apps ntfs defaults,umask=007,gid=46,noatime 0 0
# /dev/sdc5
UUID="BEDC96B5DC966803" /media/downloads ntfs defaults,umask=007,gid=46,noatime 0 0

I then performed a sudo mount -a, and i was able to access my drives.

However the drives are not showing in places or thunar side panel. I have tried adding the drives into the fstab, by UUID, LABEL and device name /dev/sdb1 etc. No matter what i do i cannot get the drives to show in places or in thunar side panel. From the little experience I have with linux i know these should show, but I aint got a clue why they aint for me. (I have rebooted a number of times during the changes made)

I have raised this question on Linux Mint forums, as well as this forum as i get the same issue with Xubuntu.  I really don't want to use Gnome and much prefare XFCE but this is very annoying to me

Any help would be appreciated.

---

