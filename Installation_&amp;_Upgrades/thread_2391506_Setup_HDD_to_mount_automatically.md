---
title: "Setup HDD to mount automatically"
date: 2018-05-10
forum: Installation &amp; Upgrades
---

### Post by stanislas-brossette on 2018-05-10
Hello,
I recently build a PC and installed ubuntu 18.04 on it. I installed 2 HDD in it, but only one is automatically mounted.
I'd like the second one to be mounted as well. Any help appreciated.
Here is the output of sudo blkid
```
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/sda1: UUID="C8C2-BEA4" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="fb5edaef-2b34-4e67-9f76-5d34f70810ef"
/dev/sda2: UUID="07a11cb8-b84f-4f35-bf75-6e668ac561c8" TYPE="ext4" PARTUUID="47c698fe-e8b2-409b-83e3-71a9f77c9d8d"
/dev/sda3: UUID="821db62e-17ad-40da-9e8f-6c9a7a7b3c61" TYPE="swap" PARTUUID="886347f6-0054-4d89-a960-4f41749c0c8f"

```

And here of sudo fdisk -l 
```
Disk /dev/loop0: 86,6 MiB, 90759168 bytes, 177264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop1: 86,6 MiB, 90828800 bytes, 177400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop2: 4,9 MiB, 5152768 bytes, 10064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 111,8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 28ECA11E-5078-4865-9C16-A69D817F902C

Device         Start       End   Sectors  Size Type
/dev/sda1       2048   1050623   1048576  512M EFI System
/dev/sda2    1050624 200980479 199929856 95,3G Linux filesystem
/dev/sda3  200980480 234440703  33460224   16G Linux swap

Disk /dev/sdb: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

```

And cat /etc/fstab 
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=07a11cb8-b84f-4f35-bf75-6e668ac561c8 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=C8C2-BEA4  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=821db62e-17ad-40da-9e8f-6c9a7a7b3c61 none            swap    sw              0       0
```

I assume that I need to add the correct line in /etc/fstab, but not sure how to write that line.
Thanks

---

### Post by yancek on 2018-05-10
Your second 1TB drive shows in your fdisk output and it has no partitions or filesystems. You mount filesystem on a device or more commonly, on a partition on a device, so there is nothing to mount.  Create a partition or several based on your needs and create a filesystem on it which you can do from the installer with GParted.  If you want them to moun on boot, you need an entry in the /etc/fstab file for each partition.

---

### Post by Dennis N on 2018-05-10
After you get the disk partitioned and partitions formatted, you can follow this short description of how to do this:

You can copy the line below and paste into **/etc/fstab** at bottom. Change the UUID to the UUID of the data partition (file system) on the 2nd drive that you want to mount. On startup, this example mounts the ext4 file system matching the given UUID at **/mnt/Data**

```
UUID=c3121154-ee33-418b-8c43-10377841e3c2 /mnt/Data ext4 defaults 0 2
```

Read UUID for your partitions (file systems) from this command:

```
lsblk -o name,UUID

```
After reboot and checking that the automount worked, change owner and group of the mount point (/mnt/Data) to you user name. Then you can use it.

If your user name is name,
```
sudo chown -R name:name /mnt/Data
```

---

### Post by oldfred on 2018-05-10
Also since sda is gpt partitioned better to use gpt partitioning for sdb.

       I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. Then add the partitions you want.
I do like to have another / (root) partition of 25GB for test or experimental installs. And I want an ESP - efi system partition on every drive, even if not directly used by Ubuntu default installs.


 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab) 

Use ext4, but you will have to give yourself ownership & permissions.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. 


 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) 
[https://ubuntuforums.org/showthread.php?t=1811198](https://ubuntuforums.org/showthread.php?t=1811198)

---

