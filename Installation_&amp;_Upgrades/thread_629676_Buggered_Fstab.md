---
title: "Buggered Fstab"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by VoiceOvGod on 2007-12-02
I have two hard drives. Gutsy will not see the second one. I have tried mounting, and get the following:

```


~$ sudo mount /dev/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

Next, I tried fsck:

```

$ fsck /media/sdb1/
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Is a directory while trying to open /media/sdb1/

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```

I really think it is my fstab that is the culprit. I am just attempting to avoid the most drastic of commands.

Here is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c7770359-8b82-46d5-af0c-bf3d9b4ae135 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8fad65bd-89ca-4017-84d1-4cedf08b3786 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/sdb1
/dev/sdb1  /media/sdb1     ext3    defaults  0    2

```

When trying to redo the partition, I get the following:

```

/$ sudo fdisk /media/sdb1
last_lba(): I don't know how to handle files with mode 40755
You will not be able to write the partition table.

Unable to read /media/sdb1

```

---

### Post by VoiceOvGod on 2007-12-02
From Ubuntu Chat:

> ok, well to use the backup suberblock, you would get a list with 'mke2fs -n /dev/sdb1' and then 'e2fsck -b NUMBER /dev/sdb1'.  Finally, you don't want to fdisk /media/sdb1, you want to fdisk a device

```


sudo mke2fs -n /dev/sdb1

mke2fs 1.40.2 (12-Jul-2007)
mke2fs: inode_size (128) * inodes_count (0) too big for a
        filesystem with 0 blocks, specify higher inode_ratio (-i)
        or lower inode count (-N).

~$ sudo e2fsck -b NUMBER /dev/sdb1
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?


```

---

### Post by merlinus on 2007-12-02
Don't know if this will help, but here is the proper mount command:

sudo mount -t ext3 /dev/sdb1 /media/sdb1

This assumes that you have already created /media/sdb1

You might also try booting from the gparted live cd and look at how sdb is partitioned.

---

### Post by VoiceOvGod on 2007-12-02
[http://i221.photobucket.com/albums/dd10/voiceovgod/gparted120207.png](http://i221.photobucket.com/albums/dd10/voiceovgod/gparted120207.png)

Screenshot of gparted running.

And for the record, it takes a LONG time for gparted to scan my system.

---

### Post by VoiceOvGod on 2007-12-02
```
~$ sudo mount -t ext3 /dev/sdb1 /media/sdb1
[sudo] password for shiva:
mount: special device /dev/sdb1 does not exist

```

---

### Post by merlinus on 2007-12-02
According to gparted, sdb1 is an extended partition, so that may be the problem.  An extended partition is meant to hold a number of logical partitions, but contains nothing on its own and cannot be formatted.

Also, the gparted graphic shows that all the space on sdb is unallocated except for the extended partition.  Ubuntu will not recognize unallocated space.

---

### Post by VoiceOvGod on 2007-12-02
Ok, so, how can I fix that?

---

### Post by VoiceOvGod on 2007-12-02
Ok, it looks like I got it, but I just want to make sure it stays mounted all the time....

```
~$ sudo mount -t ext3 /dev/sdb5 /media/sdb1

```

---

### Post by merlinus on 2007-12-02
Looks like you created a logical partition, sdb5, and formatted it as ext3??

I would change the mountpoint to avoid possible future confusion.

sudo mkdir /media/sdb5

Then add a line to /etc/fstab:

/dev/sdb5 /media/sdb5 ext3 defaults 0 2

You may wish to place it just below the entry for /

---

### Post by VoiceOvGod on 2007-12-02
Ok... I think I got it.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c7770359-8b82-46d5-af0c-bf3d9b4ae135 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8fad65bd-89ca-4017-84d1-4cedf08b3786 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/sdb1
/dev/sdb1  /media/sdb1     ext3    defaults  0    2

/dev/sdb5 /media/sdb5 ext3 defaults 0 2
```

Should I do anything about /dev/sdb1 ?

---

### Post by merlinus on 2007-12-02
Definitely delete the sdb1 line from fstab, and you may want to delete the directory as well (/media/sdb1).

---

