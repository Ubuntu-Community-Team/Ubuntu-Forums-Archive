---
title: "Unable to access new partition"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by Bucic on 2011-02-15
I've created few new ext4 partitions and weird things started to happen.

First I couldn't open neither the new partitions nor my USB pen drive even though they were listed under "Places". Nautilus simply wouldn't open. After some time it resolved itself and I could open all of them.

But then I couldn't create a new folder nor copy any files to that partitions (error: permission denied).

/etc/fstab contents:
```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
```

```
:~$ sudo fdisk -l
[sudo] password for hg1: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00092ecc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         262        2410    17257472   83  Linux
/dev/sda2            2410        9730    58795008    5  Extended
/dev/sda3               1         262     2097152   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/sda5            9208        9730     4194304   83  Linux
/dev/sda6            2410        2802     3145728   83  Linux
/dev/sda7            2802        9208    51452928   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4026 MB, 4026531840 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf027b97a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3919828+   6  FAT16

```

```
:~$ sudo blkid
[sudo] password for hg1: 
/dev/sda1: UUID="234f851a-ddd6-4e56-8adb-05fe335fdc1d" TYPE="ext4" 
/dev/sda3: UUID="188b85cc-7989-4386-a7e6-32c5f5c02cbb" TYPE="swap" 
/dev/sda5: UUID="ed0e75fa-3ebe-4597-98a8-1209c2cb7593" TYPE="ext4" 
/dev/sda6: UUID="5b9cb703-2b3a-4287-b789-9f90964b031f" TYPE="ext4" 
/dev/sda7: UUID="b215351b-0a65-45bf-99a3-d9cfd32b09eb" TYPE="ext4" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="MULTIBOOT" UUID="8CD4-97F3" TYPE="vfat" 

```

---

### Post by sikander3786 on 2011-02-15
There seem to be a problem with sda1 and sda3. But, please post the output of this command first.

```
sudo fdisk -lu
```

---

### Post by Bucic on 2011-02-15
Thanks for such a fast response! :)

```
:~$ sudo fdisk -lu
[sudo] password for hg1: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00092ecc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *     4196352    38711295    17257472   83  Linux
/dev/sda2        38711296   156301311    58795008    5  Extended
/dev/sda3            2048     4196351     2097152   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/sda5       147912704   156301311     4194304   83  Linux
/dev/sda6        38713344    45004799     3145728   83  Linux
/dev/sda7        45006848   147912703    51452928   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4026 MB, 4026531840 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf027b97a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7839719     3919828+   6  FAT16

```

---

### Post by oldfred on 2011-02-15
How are you mounting them. You need to be the owner & have permissions. Best to permanently mount with fstab.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

$ sudo mkdir /Data
$ sudo mount /dev/sda5 /Data
where sda5 needs to be your drive, partition
if not known to list partitions
sudo fdisk -l

If you cannot read and write then change the permissions. Not for NTFS

$ sudo chmod -R 777 /Data
sudo chown -R fred:fred /Data
where fred should be your login name

I prefer to manually edit as I have sometimes had issues with this:
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)
Storage Device Manager - Worry-Free Fstab Configuration
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by sikander3786 on 2011-02-15
sda3 doesn't end on cylinder boundary but that is not a serious issue.

In addition to *oldfred's* suggestion above, here is an even simpler one.

[http://ubuntu4beginners.blogspot.com/2011/01/permanently-mount-ext3ext4-drives-with.html](http://ubuntu4beginners.blogspot.com/2011/01/permanently-mount-ext3ext4-drives-with.html)

---

### Post by Bucic on 2011-02-15
I can't find that bloody PySDM. It's listed as installed in the software center.

Isn't Ubuntu supposed to auto mount new partitions anyway?

---

### Post by Bucic on 2011-02-15
I've added a line on the end of my fstab and currently it looks like this
```
/dev/sda1 / ext4 defaults 0 1
/dev/sda3 swap swap sw 0 0
/dev/sda7 /media/data ext4 defaults 0 2
```
I still can't access that sda7 partition.

I did only that (one line added). Nothing else. I used the sudo gedit /etc/fstab command. Rebooting doesn't help either.

---

### Post by oldfred on 2011-02-15
And did you chown  & chmod it?

if you look at the /media/data partition.

Mine are all folders:

```
fred@fred-LT-A105:/mnt/data$ ls -l
total 84
drwxrw-rw- 10 fred fred  4096 2011-02-07 17:40 Documents
drwxrw-rw-  2 fred fred  4096 2011-02-13 13:19 Downloads

```

---

### Post by Bucic on 2011-02-15
As I said I've only added the line in fstab.

I did chown as per the guide at blogspot linked above. One command.


It works now, however I would be grateful for additional info:
- isn't ubuntu supposed to automount partitions created post system installation?
- I recall I mounted more than one linux partition in the past and I have never even heard of chown and chmod. How is that possible? EDIT: Even this guide doesn't mention chmod/chown [http://landofthefreeish.com/linux/howto-move-home-to-its-own-partition-after-a-linux-install/](http://landofthefreeish.com/linux/howto-move-home-to-its-own-partition-after-a-linux-install/)

---

