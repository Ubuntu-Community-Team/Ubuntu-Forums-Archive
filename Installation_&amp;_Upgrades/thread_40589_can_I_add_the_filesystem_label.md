---
title: "can I add the filesystem label?"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by wxlidar on 2005-06-09
Hi all,

I had a NTFS (/dev/hdg1) partition that I wanted to convert to ext2 so I could use symbolic links. I copied everything off the partition, used fdisk to delete the partition and created a new one the same size. I then used mke2fs to format the partition. I then mounted the partition and copied the data back onto it. I worked on the files last week and even created my symbolic links.

However, I tried to access the partion today and it wasn't mounted (shut the machine down over the weekend). I tried to mount it and it gave me this:

```

 mount: wrong fs type, bad option, bad superblock on /dev/hdg1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

So I tried to specify the filesystem type without any luck. Here is what fdisk gives me:

```

Disk /dev/hdg: 100.0 GB, 100030242816 bytes
16 heads, 63 sectors/track, 193821 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1       60945    30716279+  83  Linux
/dev/hdg2           60946      121890    30716280    c  W95 FAT32 (LBA)

```

So the partition is there. So now I try parted:

```

dave@daneel:~$ sudo parted /dev/hdg check
Partition number? 1
Error: Could not detect file system.
Information: Don't forget to update /etc/fstab, if necessary.

```

and

```

dave@daneel:~$ sudo parted /dev/hdg print
Disk geometry for /dev/hdg: 0.000-95396.273 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.000  29996.367  primary
2      29996.367  59992.734  primary   fat32       lba
Information: Don't forget to update /etc/fstab, if necessary.

```

So the filesystem type is missing. Huh? Is there anyway to give it the filesystem type without losing the data on the partition? I have a backup but would lose last weeks work. :(

Thanks,
Dave

---

### Post by Joeb on 2005-06-09
How are you trying to mount the partition, manually or through fstab?  Are you specifying ext2 as the filesystem or are you telling it auto?  If auto, you might try specifying ext2 and see if that works.  If you had an fstab entry for the partition before and it was saying you were using NTFS as the files system, then that needs to be changed before you can mount the partition.


If none of that is the case then you might want to try running e2fsck and see what it says.

---

### Post by wxlidar on 2005-06-14
[QUOTE=Joeb]How are you trying to mount the partition, manually or through fstab?  Are you specifying ext2 as the filesystem or are you telling it auto?  If auto, you might try specifying ext2 and see if that works.  If you had an fstab entry for the partition before and it was saying you were using NTFS as the files system, then that needs to be changed before you can mount the partition.


If none of that is the case then you might want to try running e2fsck and see what it says.[/QUOTE]
 Thanks Joeb. I tried both methods to mount the drive. Both times specifying the filesystem type (tried ext2, ext3, resierfs, ntfs). 

Here is what e2fsck give me:
```

e2fsck 1.35 (28-Feb-2004)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/hdg1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

Any ideas?

Thanks,
Dave

---

### Post by Joeb on 2005-06-14
[QUOTE=wxlidar]Thanks Joeb. I tried both methods to mount the drive. Both times specifying the filesystem type (tried ext2, ext3, resierfs, ntfs). 

Here is what e2fsck give me:
```

e2fsck 1.35 (28-Feb-2004)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/hdg1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

Any ideas?

Thanks,
Dave[/QUOTE]

Are you sure you formatted it ext2 (or ext3)?  If so, I'd go ahead and try the command it suggests: e2fsck -b 8193 /dev/hdg1 and see what happens.  If the superblock is bad, then the backup one at 8193 might rescue you (assuming it is actually there).  If it indicates there isn't an alternate superblock at 8193, then you could run: mke2fs -n to see where it is.  At this point, you have nothing to lose (that isn't probably already gone).

---

