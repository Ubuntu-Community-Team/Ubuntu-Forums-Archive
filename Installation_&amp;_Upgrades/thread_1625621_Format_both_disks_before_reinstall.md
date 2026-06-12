---
title: "Format both disks before reinstall"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by rogerfgay on 2010-11-19
Reformatting two drives before re-installation.

I'm new to Linux generally. Can someone give me instructions on formatting the hard drives?

I have installed ubuntu on a machine that had been running Windows for a while. Since Windows worked the boot drive for years, I decided to switch the positions of the two drives; putting the old data drive into the boot position.

Apparently, ubunta was too smart for me. I guess it discovered the Windows installation, and decided that's where it should be installed too. Now, what I would like to do - and I would really like to do it this way - is reformat both the disks, wiping out everything that's on both of them; before running another installation.

BTW: the old data drive is still NTFS, and I don't want installations own both disks - reformatting and starting fresh seems nice and clean, if not entirely necessary.


        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi4
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:18c8(size=8) ioport:18ac(size=4) ioport:18c0(size=8) ioport:18a8(size=4) ioport:18b0(size=16) memory:de304400-de3047ff
           *-disk:0
                description: ATA Disk
                product: ST9120821AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 7.24
                serial: 5PL35K3F
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=677053da
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: eab5b741-7bb2-c143-a33a-e42417e6750f
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-04-29 06:53:46 filesystem=ntfs label=Data state=clean
           *-disk:1
                description: ATA Disk
                product: ST9120821AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/sdb
                version: 7.24
                serial: 5PL30822
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000527cc
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: b0fcc4bb-8eb3-4dbc-a8a8-49263b78c86e
                   size: 107GiB
                   capacity: 107GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-11-17 17:46:12 filesystem=ext4 lastmountpoint=/ï¿½<ï¿½ï¿½ïï¿½ï¿½ï¿½ï¿½ï¿½ïï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½Pï¿½rï¿½ï¿½l!ï¿½ï¿½ï¿½ï¿½ï¿½@ï¿½rï¿½h,ï¿½h,ï¿½ï¿½ï¿½ï¿½ï¿½hï¿½rï¿½yo!ï¿½ï¿½d modified=2010-11-18 08:39:05 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-11-18 17:09:54 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@4:0.0.0,2
                   logical name: /dev/sdb2
                   size: 4693MiB
                   capacity: 4693MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 4693MiB
                      capabilities: nofs

---

### Post by dino99 on 2010-11-19
what you need:

use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernation is used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

