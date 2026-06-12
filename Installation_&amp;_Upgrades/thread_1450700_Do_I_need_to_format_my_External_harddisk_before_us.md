---
title: "Do I need to format my External harddisk before using it ?"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2010-04-09
I have just got a new external harddisk.
I used it strait in window I copy some files on it. without formating it.
Now when I use ubuntu it said that it is total only 10Giga, but the external harddisk is 1000 Giga.
How come ? is htis because it has to be formated before ubuntu se the total size ?

---

### Post by oldfred on 2010-04-09
What does disk utility and gparted see? also 
```
sudo fdisk -l
```

I did not think you could even copy files to an unpartitioned drive, but someone posted some info several weeks back. The MBR drive scheme requires partitions and format of each partition. Are you sure it was not preformatted for windows or windows formated it?

IF it is a new large drive you need to plan partitions depending on how you want to use it. One large partition often is not the best even if you only want to store data.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

---

### Post by srs5694 on 2010-04-09
First, some terminology clarification:


[list]
[*]Format -- A vague and nebulous term that people use to refer to any of the below.
[*]Low-level format -- Creating data structures on the disk that mark out the start and end points of individual sectors. This is done at the factory for hard disks, and modern hard disks don't usually permit low-level formats. It's possible to do low-level formats of floppy disks using the fdformat utility, though.
[*]High-level format -- synonymous with "creating a filesystem" (see below).
[*]Partitioning -- Marking out large chunks of a disk for use by different OSes, filesystems, or other tools. Hard disks are usually partitioned, but this isn't strictly necessary if you just want to use one big filesystem on the disk. In Linux, partitioning is done with tools such as fdisk, gdisk, parted, or GParted.
[*]Creating a filesystem -- Disks or partitions must contain filesystem data structures before you can put files on the disk. This is done with tools such as mkfs, parted, or GParted.
[/list]


Store-bought external disks may come unpartitioned and with no filesystem; partitioned for one partition and with a filesystem (probably FAT or NTFS); unpartitioned and with a filesystem (probably FAT or NTFS); or theoretically in other forms. If the disk was used in Windows to store files, then it does have a filesystem on it, but whether it's partitioned or not is another matter. The fdisk command that oldfred recommends will show the partitions, if present, on the disk. If fdisk reports that there are no partitions, then the disk almost certainly has a "raw" filesystem on it. I don't know offhand if Ubuntu will automatically detect this configuration. If not, it should be possible to manually mount the disk using a text-mode command:

```

sudo mount /dev/sdb /mnt

```

Change /dev/sdb, if necessary, and change /mnt to an appropriate mount point if you don't like /mnt for this purpose. Adding options can adjust permissions and other features. (Type "man mount" to read about these options.)

---

