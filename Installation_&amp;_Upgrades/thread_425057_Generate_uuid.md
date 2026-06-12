---
title: "Generate uuid"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by avelldiroll on 2007-04-27
Hi all,

I "experienced" (euphemism) a power outage during an upgrade from edgy to feisty. I managed to finish the upgrade in console mode after the system restarted (I for one welcome our apt database overlords).

However a last problem bugged me ... 
On this particular system, I have 2 IDE disks, and only one was declared with uuid, the other one (hdb under edgy, sdb now), where /home is, was not included in /etc/fstab (i added it manually).

$ sudo fdisk -l
```

Disk /dev/sda: 40.0 GB, 40000020480 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          24      192748+  83  Linux
/dev/sda2              25         146      979965   82  Linux swap / Solaris
/dev/sda3             147        3185    24410767+  83  Linux
/dev/sda4            3186        4863    13478535   83  Linux

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4866    39086113+  83  Linux

```

$ cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=854ef599-fee5-4fd9-a1d8-260e09cee389 / ext3 defaults,user_xattr,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=961303b5-fcf6-4ced-93e6-437cfd9ecf1f /boot ext2 defaults 0 2
/dev/sdb1       /home           ext3    defaults,user_xattr        0       2
# /dev/hda4 -- converted during upgrade to edgy
UUID=6c24d327-5b69-4176-a45a-138108a7c969 /mnt/backup ext3 defaults,users,user_xattr 0 2
# /dev/hda2 -- converted during upgrade to edgy
UUID=ea309874-0a18-4370-9e53-1400f44ba8af none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

$ ls -lh /dev/disk/by-uuid/ 
```

total 0
lrwxrwxrwx 1 root root 17 2007-04-27 11:15 6c24d327-5b69-4176-a45a-138108a7c969 -> ../../mapper/sda4
lrwxrwxrwx 1 root root 17 2007-04-27 11:15 854ef599-fee5-4fd9-a1d8-260e09cee389 -> ../../mapper/sda3
lrwxrwxrwx 1 root root 17 2007-04-27 11:15 961303b5-fcf6-4ced-93e6-437cfd9ecf1f -> ../../mapper/sda1
lrwxrwxrwx 1 root root 17 2007-04-27 11:15 ea309874-0a18-4370-9e53-1400f44ba8af -> ../../mapper/sda2

```

$ sudo vol_id  /dev/sdb1
```

ID_FS_USAGE=raid
ID_FS_TYPE=LVM2_member
ID_FS_VERSION=LVM2 001
ID_FS_UUID=
ID_FS_LABEL=
ID_FS_LABEL_SAFE=

```

$ sudo vol_id  /dev/sda1
```

ID_FS_USAGE=filesystem
ID_FS_TYPE=ext2
ID_FS_VERSION=1.0
ID_FS_UUID=961303b5-fcf6-4ced-93e6-437cfd9ecf1f
ID_FS_LABEL=/boot
ID_FS_LABEL_SAFE=boot

```


This system was upgraded to the last ubuntu since hoary, and I believe lvm was not default at that time, that is why no lvm was defined so far.

I think that the power outage is the cause of my problem ... and everything is working without using uuid for sdb1 so i should not bother ... but I would prefer to standardise to uuid.

So finally my question is: do you know how to generate uuid? or why it consider an IDE disk as RAID? or any idea of what is missing?
I would also appreciate any pointers to some google uuid references/manual/hoiwto/faq ... i remeber seeing a nice howto 2 months ago, but I am not able to find it any more ... 

Thanks in advance.

---

### Post by avelldiroll on 2007-05-02
So ... what happened so far ... not much because I had other stuff to take care of.

I was surprised to ged an UUID for sdb1 wheen using blkid ...
And to reply to my first question, one can generate a UUID using ... uuidgen
and this new UUID may be assigned to a disk using tune2fs -U
But this did not solve my problem and I start wondering why the ID_FS_USAGE of sdb1 is set to raid (it was never used in a raid array) ... I really don't know how a power shortage may set a flag on a disk.
However it might offer a hint ... the LFS documentation suggests creating UUID symlink only when ID_FS_USAGE is set to either filesystem or other.
So I now need to find a way to set ID_FS_USAGE to filesystem on sdb1 ... but a little googling did not helped so far.

---

