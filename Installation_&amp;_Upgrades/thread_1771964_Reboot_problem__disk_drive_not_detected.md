---
title: "Reboot problem : disk drive not detected"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by nuox012 on 2011-05-30
Evertime i try to reboot, it appears on screen that " The disk drive for /usr/local is not ready yet or not present" . I need to press S to skip mounting to enter ubuntu. I am using ubuntu 10.10 . Any idea to solve this ?

---

### Post by Toz on 2011-05-30
Can you post back the contents of your /etc/fstab file?

And the results of```
sudo blkid
```

---

### Post by nuox012 on 2011-05-30
How to do that ? I'm new to ubuntu. sorry

---

### Post by Toz on 2011-05-30
Open a terminal window and type in:```
cat /etc/fstab
```

and ```
sudo blkid
```

Whatever results come back, copy and paste back here.

---

### Post by nuox012 on 2011-05-30
is this what are you looking for ?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext2    errors=remount-ro 0       1
# /usr/local was on /dev/sda6 during installation
UUID=01f11320-0932-4975-a923-b09952d743f1 /usr/local      ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=606c8900-87be-48ba-99c9-c4842b3143ad none            swap    sw              0       0

---

### Post by nuox012 on 2011-05-30
for sudo blkid

/dev/sda1: UUID="192d7672-4677-4545-a271-9cf73b3dfba3" TYPE="ext2" 
/dev/sda5: UUID="606c8900-87be-48ba-99c9-c4842b3143ad" TYPE="swap" 
/dev/sda6: UUID="0F6AE6391592D483" TYPE="ntfs"

---

### Post by Toz on 2011-05-31
And:```
sudo fdisk -l
```

What is your sda6 partition? What's there? Mounted to /usr/local.

---

### Post by nuox012 on 2011-05-31
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001b43a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24316   195311616   83  Linux
/dev/sda2           24316       60802   293072897    5  Extended
/dev/sda5           24316       25532     9764864   82  Linux swap / Solaris
/dev/sda6           25532       60802   283307008    7  HPFS/NTFS

Disk /dev/sdb: 8036 MB, 8036286464 bytes
39 heads, 39 sectors/track, 10319 cylinders
Units = cylinders of 1521 * 512 = 778752 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2       10320     7846836    b  W95 FAT32


There's nothing in sda6. Just not so important files right there. 
Is that the main problem why it happens like this ? Before i started changing that sda6, ubuntu booting was okay. How to fix that ?

---

### Post by oldfred on 2011-05-31
It looks like you changed sda6 to NTFS. All Linux system partitions have to use Linux formats. Windows formats like FAT & NTFS do not support permissions & ownership.

Was there some reason to have /usr/local on a separate partition?

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by nuox012 on 2011-05-31
I deleted the NTFS and try to reboot. It still need me to press S before i can enter ubuntu. Now the file system for sda6 is unallocated. And also combining all the partitions into one might be the best solution. How to do that using Gparted Partition Editor ?

---

### Post by oldfred on 2011-05-31
If you had any data in /usr/local it is now gone.

If you did not have any data, just edit fstab to remove the enty. Not sure if it will automaticallly recreate all the folders or not. I see 10 sub folders in my system, but most are empty and a couple are things I created.

gksudo gedit /etc/fstab

Put a # in front of the entry to convert to a comment.

Always run this after any edit to fstab. If it just returns it is ok. If you have any errors you must fix before rebooting or you may not be able to reboot.

sudo mount -a

---

