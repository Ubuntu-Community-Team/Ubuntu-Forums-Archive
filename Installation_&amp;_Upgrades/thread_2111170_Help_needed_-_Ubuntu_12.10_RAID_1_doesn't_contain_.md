---
title: "Help needed - Ubuntu 12.10 RAID 1 doesn't contain valid partition table"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by jostar on 2013-02-01
Hi, I'm new to Ubuntu and am trying to setup my N40L using 250GB as OS plus 2x2TB as RAID 1 for data. However am running into problem during toward the second half of installation.

A brief summary of what I have done.

N40L running single 250GB HD (/dev/sdc), created bootable USB and install Ubuntu to the single 250GB HD using all default settings. Everything was straight forward, also managed to install Samba and worked perfectly.

Shut down computer, then install 2x2TB drives, start up computer.

Installed GParted, can see the new drives (/dev/sda & /dev/sdb). In Gparted, formatted to ntfs. I know that ntfs may not be the best format, but was keeping my option open just in case I want to turn the N40L into a HTPC and I may need to put windows in it.

All seems ok and ventured into terminal.
sudo mdadm --create --name=raidarray --verbose /dev/md1 --raid-devices=2 --level=1 /dev/sda1 /dev/sdb1

md1 seems to have created successfully, then

sudo mdadm --detail /dev/md1

I suppose that initialised the array, off for the night. The next day, booted up the computer realising md1 is now md127 and read only, googled it and rectify with following:
sudo mdadm --stop /dev/md127
sudo mdadm --assemble --verbose /dev/md1 --level=1 /dev/sda1 /dev/sdb1
then amended mdadm.conf
sudo update-initramfs -u

At this point I have not restarted the machine to test if the array would remain after the boot and I ran into my currect problem after I did
sudo fdisk -l

and this is what I got
```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00018e6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  3907028991  1953513472    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00080f77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472    7  HPFS/NTFS/exFAT

Disk /dev/md1: 2000.3 GB, 2000263380992 bytes
2 heads, 4 sectors/track, 488345552 cylinders, total 3906764416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dd73b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      499711      248832   83  Linux
/dev/sdc2          501758   488396799   243947521    5  Extended
/dev/sdc5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/mapper/ubuntu-root: 243.5 GB, 243491930112 bytes
255 heads, 63 sectors/track, 29602 cylinders, total 475570176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 6304 MB, 6304038912 bytes
255 heads, 63 sectors/track, 766 cylinders, total 12312576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table
```I seems that I am missing partition tables left right and centre, attempted to to fix the array first, did a lot of googling. and tried 
sudo e2fsck -cc /dev/md1

```
e2fsck 1.42.5 (29-Jul-2012)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/md1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;
```So didn't work, read somewhere else and suggested this:
sudo mkfs.ntfs /dev/md1

At least now it says NTFS volume structure completed, but then when I fdisk again

```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00018e6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  3907028991  1953513472   fd  Linux RAID autodetect

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00080f77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472   fd  Linux RAID autodetect

Disk /dev/md1: 2000.3 GB, 2000263380992 bytes
2 heads, 4 sectors/track, 488345552 cylinders, total 3906764416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

    Device Boot      Start         End      Blocks   Id  System
/dev/md1p1   ?     6579571  1924427647   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not start on a physical sector boundary.
/dev/md1p2   ?  1953251627  3771827541   909287957+  43  Unknown
Partition 2 does not start on a physical sector boundary.
/dev/md1p3   ?   225735265   225735274           5   72  Unknown
Partition 3 does not start on a physical sector boundary.
/dev/md1p4      2642411520  2642463409       25945    0  Empty

Partition table entries are not in disk order

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dd73b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      499711      248832   83  Linux
/dev/sdc2          501758   488396799   243947521    5  Extended
/dev/sdc5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/mapper/ubuntu-root: 243.5 GB, 243491930112 bytes
255 heads, 63 sectors/track, 29602 cylinders, total 475570176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 6304 MB, 6304038912 bytes
255 heads, 63 sectors/track, 766 cylinders, total 12312576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition 
```At least now /dev/sdb1 & /dev/sdc1 are showing as Linux RAID! But md1 has got 4 partitions, and it doesn't even look like a partition table? Another thing is when I go into GParted now, both /dev/sdb1 & sdc1 can not be reckonised and file system says 'unknown'. I think I have stuffed it up pretty badly.

So I did more google, someone suggested to do a clean reinstall of the RAID by wiping the array and start over, build the array first and then format. What are the steps and commands to do that including wiping the array?

Another question is fdisk also showing /dev/mapper/ubuntu-root and  /dev/mapper/ubuntu-swap_1 don't have a valid partition either. Is that  something I need to worry about?

Sorry for the long post, any help is much appreciated.

---

### Post by darkod on 2013-02-01
You should have focused on few questions only. In this long post I got lost what's your problem.

Is the system working fine?

If you are getting confused by the fdisk messages about /dev/md1 and the LVs /dev/mapper/..., then you have nothing to worry about. fdisk can't look inside mdadm and LVM, so it reports those messages about the partition table. Ignore them.

It's better to use parted for command line partitioning than fdisk in any way.

Also, why would you do mkfs.ntfs /dev/md1. Why would you want ntfs filesystem on SW raid device?

---

### Post by jostar on 2013-02-01
Once again sorry for the long post, was hoping to layout the whole history of what happen so it's clearer on what I may have done wrong.

I did NTFS because I maybe using the machine as HTPC down the road, and if that is the case I may need to run windows. Correct me if I am wrong, by formatting the drives NTFS I was hoping that if I do downgrade to windows OS, then the RAID 1 data drives can be read by windows right away.

The system is working fine at the moment, but I am not sure if there will be any issue lurking around the corner. My main concerns are the integrity of the RAID array. I am seeing multitude of errors in fdisk including where it descript the RAID partition table as "This doesn't look like a partition table", Gparted is not seeing the RAID drives even the documentation says it should and when I do ls -l md1p4 is no where to be seen. So I am very concern that I did not set up the RAID properly.

Considering wiping the the drives /sda & /sdb and start over again maybe in ext3 if need be. However don't know what are the steps/commands that I need to wipe and start again properly.

I want to be sure the array is working properly before I put critical data in it.

---

### Post by darkod on 2013-02-01
You are wrong about the ntfs. Yes, the partition(s) on the md devices might be ntfs but the md device is a linux SW raid device which windows can't understand. If you install windows on the OS disk, the data disks are as good as blank as far as windows is concerned.

I'm not sure if HTPC will actually need to have windows software running on it, but if you only need media server/streaming, this is easily done with linux.

My ubuntu home server runs Server 12.04 LTS and Twonky which acts as media server for my Samsung TV.

It all depends what and how you will use it for. Windows machines can access Samba shares as a network shared location, other media devices can access Twonky or MiniDLNA (free) for example. If you need other things, you might need windows and windows software.

One thing is for sure, don't count that a windows installation will just pick up the mdadm raid disks and keep on going.

As for the ls md1p4, it can't work like that. You use ls with a mount point, like if you have /dev/md1 mounted at /data, you would do ls /data.

You can't read the partition directly, you can read the filesystem on it. I'm not aware of any command that can list the content by using the device name.

The first point to look for the mdadm integrity is:
cat /proc/mdstat

If that says all md devices are active, and all disks present (the syntax is (UU) as opposed to (U_) for example), it looks good. If you have an U missing, that usually means disk missing from the array.

---

### Post by jostar on 2013-02-01
My current plan is to use Plex and stream content to other laptops and a roku is on the shopping list. Direct connection to a dumb TV is another project all together.

You have a very good point on ntfs being a Linux RAID that I didn't consider. Any case I am more comfortable wiping the discs and starting over again, maybe this time should be in ext3 file system.

So what is the correct way of doing it? How do I do a low level format? With the extra reserach I have been doing it seems the correct steps would be:
Stop Mdadm
perform low level format of the discs without file system (how to do that?)
sudo mdadm --create --name=raidarray --verbose /dev/md1 --raid-devices=2 --level=1 /dev/sda1 /dev/sdb1
mkfs.ext3 /dev/md1
amended mdadm.conf
sudo update-initramfs -u

Is that correct?

---

### Post by darkod on 2013-02-01
You already have mdadm in place. You don't need to do any of that, just format md1 with ext4 or ext3. I don't know if you prefer ext3, the latest version is ext4. So, it would be like:
sudo mkfs.ext4 /dev/md1

Of course, that would delete all data on it.

I forgot to mention, you don't need to stop md1 but you do need to unmount it in order to format it. So, before the mkfs command you would need to do something like:
sudo umount /mount-point

After that remount it again and you can use it. Check fstab after the formatting. If you have /dev/md1 in there (the default case), it should be fine. If you have UUID instead of /dev/md1, you will need to replace it with the new UUID after the format.

---

### Post by jostar on 2013-02-20
Been busy for a few weeks, finally have time to look at the server again. Formatted /md1 in ext3 and it seems to be ok using cat /proc/mdstat

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda1[0] sdb1[1]
      1953382208 blocks super 1.2 [2/2] [UU]
      
But then still getting the same error of not having a valid partition table when I do a fdisk.

```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00018e6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  3907028991  1953513472   fd  Linux RAID autodetect

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00080f77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472   fd  Linux RAID autodetect

Disk /dev/md1: 2000.3 GB, 2000263380992 bytes
2 heads, 4 sectors/track, 488345552 cylinders, total 3906764416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dd73b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      499711      248832   83  Linux
/dev/sdc2          501758   488396799   243947521    5  Extended
/dev/sdc5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/mapper/ubuntu-root: 243.5 GB, 243491930112 bytes
255 heads, 63 sectors/track, 29602 cylinders, total 475570176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 6304 MB, 6304038912 bytes
255 heads, 63 sectors/track, 766 cylinders, total 12312576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table

```Is that normal?

---

### Post by darkod on 2013-02-20
Yes, it is. The md and LVM devices are not exactly physical disks, so there is no partition table on them literary speaking. So, that message is correct and normal.

Don't worry, linux knows what to do with mdadm and LVM, despite that message it will work fine. If you list all disks with parted for example, it will not complain like fdisk:
sudo parted -l

---

### Post by jostar on 2013-02-22
Ok thanks for all your help.

---

