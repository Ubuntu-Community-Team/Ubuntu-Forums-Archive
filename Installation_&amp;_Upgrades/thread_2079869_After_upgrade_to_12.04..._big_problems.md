---
title: "After upgrade to 12.04... big problems"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by semsaudade on 2012-11-02
Hi to all. Today I upgraded my Ubuntu to last version 12.04 on my netbook Asus Eeepc 900. After reboot, I obtain a message of

The disc drive for / is not ready yet or not present 
Press M for manual rescue

If I press M, I get the prompt of terminal, but I don't know what to do next.

I think the problem is that my netbook has 2 ssd drives: one 4GB drive and one 16 GB. In order to have more space for my applications, I installed Ubuntu on 16 GB drive, while leaving 4 GB drive for my documents.

Now it seems that upgrading have caused a mess with mounting point on my two drives.

What can I do? Any suggestion?

Thank a lot in advance for your help.
Giancarlo - Italy

---

### Post by semsaudade on 2012-11-03
Nobody around? I made some trials and got these results (maybe they could be useful to somebody more expert than me). Please help me!

```

#fdisk -l

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes/512 bytes
I/O size (minimum/optimal): 512 bytes/512 bytes
Disk identifier: 0xd8cbd8cb

Device        Boot Start   End    Blocks         Id     System
/dev/sda1    *       1      490    3935893+    83    Linux


Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes/512 bytes
I/O size (minimum/optimal): 512 bytes/512 bytes
Disk identifier: 0x0000db0d

Device        Boot Start   End    Blocks         Id     System
/dev/sdb1    *       1      1962    15759733+    83    Linux

#mount -l
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)

mount: warning: /etc/mtab is not writable (e.g. read-only filesystem).
It is possible that information reported by mount (8) is not
up to date. For actual information about system mount points
check the /proc/mounts file.

```

---

### Post by darkod on 2012-11-03
Post the output of this:
```
cat /etc/fstab
sudo blkid
```

---

### Post by semsaudade on 2012-11-05
Here it is:

```

#cat /etc/fstab
# <filesystem> <mount point> <type> <options> <dump> <pass>
proc    /proc   proc    defaults   0 0
# / was on /dev/sdb1 during installation
UUID=26f8f790-ccd2-4a8e-9f7a-9f2664c25783 /   ext4  errors=remount-ro 0 1
# /home was on /dev/sda1 during installation
UUID=cf17fbbf-0734-45be-9b1f-121e3e74fa5c /home  ext4  defaults,user_xattr   0   2


#blkid
/dev/sda1: UUID="cf17fbbf-0734-45be-9b1f-121e3e74fa5c"
/dev/sda2: UUID="26f8f790-ccd2-4a8e-9f7a-9f2664c25783"


```

Thanks again

---

### Post by darkod on 2012-11-05
As you can see, the UUID strings in fstab are correct (I wanted to check if they are wrong maybe).

But there is one interesting thing in the blkid output. You have two small SSDs, /dev/sda and /dev/sdb. Both of then have a single ext4 partition on them, /dev/sda1 and /dev/sdb1.

But blkid seems to think the partitions are /dev/sda1 and /dev/sda2, like they are two partitions on the same disk. It is either confused, or the disks were (are) actually merged so that they appear to the netbook as one. If that is true, maybe that's where the confusion and the error come from.

Do you remember if the storage was originally displayed as a single partition?

---

### Post by semsaudade on 2012-11-05
Thanks darkod for your kindness.

Sorry for the mistake! I made a mistake copying from terminal. The correct output (I checked it now) is:

```

#blkid
/dev/sda1: UUID="cf17fbbf-0734-45be-9b1f-121e3e74fa5c"
/dev/sdb1: UUID="26f8f790-ccd2-4a8e-9f7a-9f2664c25783"

```

So what else can I try?

---

