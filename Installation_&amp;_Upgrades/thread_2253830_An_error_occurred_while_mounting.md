---
title: "An error occurred while mounting /"
date: 2014-11-22
forum: Installation &amp; Upgrades
---

### Post by m4rky on 2014-11-22
Hello,

for no reason I have not been able to boot Ubuntu 14.04 today. Splash screen at first displayed "An error occurred while mounting /".

I tried to do filesystem check:
```

ubuntu@ubuntu:~$ sudo fsck.ext4 -cf /dev/sda1
e2fsck 1.42.9 (4-Feb-2014)
Checking for bad blocks (read-only test): done                                                 
Ubuntu: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

Ubuntu: ***** FILE SYSTEM WAS MODIFIED *****
Ubuntu: 651168/6832128 files (0.9% non-contiguous), 17733945/27304931 blocks
```

And here is my fstab file:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=89bdbb1b-ffb5-4708-b733-6de73bfae36f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
#UUID=df5a6ac8-3fe7-427e-bb7e-b7c5051bcbd8 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

Now, if I try to boot it, this splash screen flashes only for a split of second. Then black screen displays and system does not respond to anything. 

Does anybody have any ideas how to fix it?

Thank you!
Tomas M.

---

