---
title: "Filesystem Check"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by Irony on 2006-11-15
I often copy distros from one partition to another when experimenting with them.

However I've found that if I copy a distro to hda11 or higher then I get the following message on boot-up, so I can't boot up;

[PHP]Checking filesystems
/dev/hda11
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock.
   e2fsck -b 8193 <device>

fsck.ext3 : No such file or directory while trying to open /dev/hda11
Failed to check filesystem.  Do you want to repair the errors? (Y/N)
(beware, you can lose data)[/PHP]

I can't get beyond this point, it happens whether I copy root or home to hda11 or higher. I've run;

[PHP]irony@ubuntu:~$ sudo fsck.ext3 /dev/hda11
e2fsck 1.38 (30-Jun-2005)
/dev/hda11: clean, 11/1310720 files, 73945/2620595 blocks[/PHP]

and forced a check;

[PHP]irony@ubuntu:~$ sudo fsck.ext3 -f /dev/hda11
e2fsck 1.38 (30-Jun-2005)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/hda12: 4390/1310720 files (1.0% non-contiguous), 178764/2620595 blocks[/PHP]

but this makes no difference. Does anyone know how to correct this error so distros in hda11 or higher will boot up?

---

### Post by Irony on 2006-11-16
I partially got round the problem by moving some data in hda8 to hda11 - thus freeing up hda8 to use as home.

However I still have the problem that hda11 and above can't accept root or home partitions for booting up.

Note that hda11 and above work fine as partitions for folders and such - its just that they won't boot root or home if its in there.

---

### Post by Irony on 2006-11-17
I have root on hda10 and home on hda8 - these both work.

I've made an exact copy of root on hda6 and home hda12 - on hda12 I first ran;

[PHP]mkfs.ext3 /dev/hda12[/PHP]

Then did;

[PHP]irony@ubuntu:~$ sudo fsck.ext3 -b 98304 /dev/hda12
e2fsck 1.38 (30-Jun-2005)
/dev/hda12 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/hda12: ***** FILE SYSTEM WAS MODIFIED *****
/dev/hda12: 11/1310720 files (0.0% non-contiguous), 73945/2620595 blocks[/PHP]

I then did;

```
sudo cp -ax /mnt/hda8_home/* /mnt/hda12_home
```

I'll see whether that works on next boot-up... if it doesn't I'm out of ideas at the moment.

---

