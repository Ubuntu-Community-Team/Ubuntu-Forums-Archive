---
title: "fsck dies"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by radicaledward on 2007-03-19
On boot, with out fail, fsck gives:

```
Log of fsck -C -R -A -a 
Mon Mar 19 17:22:53 2007

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=1fbca371-3e0c-4ddc-a28c-c07b6b3df492'

fsck died with exit status 8

Mon Mar 19 17:22:53 2007
----------------
```

It launches a command line. Ctrl+D and ubuntu boots as normal. Any help is appreciated!

Here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=db7a7569-1828-4c5b-bd55-fb9b7008effa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=1fbca371-3e0c-4ddc-a28c-c07b6b3df492 /media/sda1     ext3    defaults        0       2
# /dev/sdb5
UUID=fd150538-d12e-485b-a26f-2c4c7449ce36 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by simonn on 2007-03-19
[http://ubuntuforums.org/showthread.php?p=1714980](http://ubuntuforums.org/showthread.php?p=1714980)

---

### Post by radicaledward on 2007-03-19
The UUIDs are the same/valid.

```
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          **1fbca371-3e0c-4ddc-a28c-c07b6b3df492**
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal filetype needs_recovery sparse_super
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              9781248
Block count:              19537040
Reserved block count:     976852
Free blocks:              19197289
Free inodes:              9781237
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Last mount time:          Mon Mar 19 16:22:54 2007
Last write time:          Mon Mar 19 16:22:54 2007
Mount count:              10
Maximum mount count:      30
Last checked:             Wed Dec 31 17:00:00 1969
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Journal backup:           inode blocks
Journal size:             128M

```

---

### Post by simonn on 2007-03-19
I always found UUIDs flakey, so I use /dev/?d?? in fstab.

---

### Post by domzo on 2007-03-22
Do you have another operating system installed on /dev/sda1 ?

Boot it up and see what that operating system thinks the UUID of /dev/sda1 is.
If it is different try and use it in your Ubuntu fstab table instead of the broken one.

I just had this same problem with a Kubuntu/Xubuntu dual boot and this solved it for me.

---

