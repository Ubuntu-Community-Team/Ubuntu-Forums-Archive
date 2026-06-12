---
title: "Partitioning and stuff"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by Ge64 on 2008-03-05
Hey,

I'm installing a tripleboot on my Macbook Pro (the fact that it's a mac is irrelevant here though), but I want Ubuntu to be on an external flashdrive (or harddrive if 4GB won't do). I have one ZFS filesystem on the Mac's hd I want to use for /home and swap, but not only for that. I actually want to use the partition for more than just ubuntu, so is there a way to point /home to /zfs/home (/zfs being the zfs partition) rather than /zfs, and how would I set up a swap file on that same drive? 

I can't have a swap partition because I wouldn't have the space on the flashdrive and I can only have 3 partitions on the hd (one for leopard, one for xp).

I'm planning to use either version 8 or 7.10, whichever you recommend (probably 8 though)

---

### Post by dstew on 2008-03-05
You might be able to create a symbolic link from the /home directory that will be part of the Ubuntu filesystem on the external flashdrive to the /zfs/home folder on your internal hard drive. You would have to put the /zfs drive into your fstab so it gets mounted before you try to run any local scripts from the linked /home folder, but it might work.

---

### Post by Ge64 on 2008-03-05
During setup you can always chose separate partitions for /home and /boot etc, can't you make it use a subfolder on a partition for these mount points instead?

---

### Post by dstew on 2008-03-05
Let's think about that. A mount point is a directory inside your root file system to which a device is attached. A device is usually a partition. You can certainly assign separate partitions to the mount points /home and /boot. But, can you assign a folder within one of those partitions to those mount points? I don't think so. That is because you are mounting *devices* to the mount points, and a folder is not a device. The command mount is what attaches a device to a mount point, and that command cannot take a directory as its first argument. It needs a device.

But, you can do an easy experiment to see if that might work. If you have two separate linux disks, and your root file system is on /dev/sda1, you could try to mount a folder that is on /dev/sdb1 to a mount point in the root file system. For example, let's say you have a directory on your root file system that you name /test_dir. Create a mount point for it on your root file system:```
sudo mkdir /mnt/test_dir
``` Then, your mount command might be```
sudo mount -t ext3 /dev/sdb1/test_dir /mnt/test_dir
```If that works, then you can mount a folder onto your /home mount point. My guess is that it will return an error that /dev/sdb1/test_dir is not a device.

---

### Post by Ge64 on 2008-03-06
> **dstew said:**
> Let's think about that. A mount point is a directory inside your root file system to which a device is attached. A device is usually a partition. You can certainly assign separate partitions to the mount points /home and /boot. But, can you assign a folder within one of those partitions to those mount points? I don't think so. That is because you are mounting *devices* to the mount points, **and a folder is not a device.** The command mount is what attaches a device to a mount point, and that command cannot take a directory as its first argument. It needs a device.

But, you can do an easy experiment to see if that might work. If you have two separate linux disks, and your root file system is on /dev/sda1, you could try to mount a folder that is on /dev/sdb1 to a mount point in the root file system. For example, let's say you have a directory on your root file system that you name /test_dir. Create a mount point for it on your root file system:```
sudo mkdir /mnt/test_dir
``` Then, your mount command might be```
sudo mount -t ext3 /dev/sdb1/test_dir /mnt/test_dir
```If that works, then you can mount a folder onto your /home mount point. My guess is that it will return an error that /dev/sdb1/test_dir is not a device.

Can a file be a device though? I think I just read something where zpool was used to create a ZFS volume from two files on an existing volume (for testing), and if I could then point that ZFS filesystem to mount as /home then I could just make a single file on the already existing ZFS filesystem for this purpose. I wonder if that would work though, I might try it all out and see.

---

### Post by jken146 on 2008-03-06
Everything is a file.  Devices are represented by files which exist within the file system, under /dev/ -- from this point of view, I think you can pick any directory you like and mount it somewhere.  Give it a try in the live CD first if you're unsure.

Example:

```
cd /media

sudo mkdir mountPoint

sudo mount /dev/sda2/home mountPoint
```
replacing sda2 with whatever partition it is you want.

---

### Post by dstew on 2008-03-06
> Everything is a file.Yes, but only when the device is mounted.

So, I did the experiment. Here is my fdisk output:> Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           2       16033+  a0  IBM Thinkpad hibernation
/dev/hda2   *           3        1412    11325825    c  W95 FAT32 (LBA)
/dev/hda3            1413        2330     7373835   83  Linux
/dev/hda4            2331        2432      819315   82  Linux swap / Solaris
This command mounts my /dev/hda2 partition to the Linux root file system mount point /media/hda2:```
sudo mount /dev/hda2 /media/hda2
```Now, I look into the mounted /dev/hda2 file system, and see the directory winnt:```
ls -l /media/hda2
```Here is the output:> ...
-rwxr-xr-x  1 root root      1024 2004-10-16 12:01 UserInfo.dat
-r-xr-xr-x  1 root root        98 2001-03-12 15:42 version.inf
drwxr-xr-x 45 root root     16384 2001-03-12 15:52 winnt
-rwxr-xr-x  1 root root      1653 2007-08-04 23:17 wsreg32.log
-rwxr-xr-x  1 root root         0 2001-10-01 11:21 wsremote.id
So, let's see if I can mount the directory winnt to the root file system. After unmounting the /dev/hda2 partition, I try```
donn@donn-laptop:~$ sudo mount /dev/hda2/winnt /media/hda2
mount: special device /dev/hda2/winnt does not exist
       (a path prefix is not a directory)

donn@donn-laptop:~$ 

```The mount command takes a device and makes it into a file, but it cannot mount a directory. The best way to have a common home directory is to create a symbolic link in your root directory, call it /home, but the link will point to the /home directory in another partition. Of course, that other partition will need to be mounted first.

---

