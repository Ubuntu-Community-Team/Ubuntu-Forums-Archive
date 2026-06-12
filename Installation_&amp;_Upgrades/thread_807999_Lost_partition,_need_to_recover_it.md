---
title: "Lost partition, need to recover it"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by elashish on 2008-05-26
So I decided to try Fedora and after the install, I found that all my partitions had been changed - most importantly, I lost my data partition (I could care less about the rest) - here's how it looks roughly:

Before:
--14GB ntfs (Windows XP)
--10GB ext3 (ubuntu)
--swap
--75GB ext3 (data)

After:
--14GB ntfs (Windows XP)
--190MB ext3? (Fedora)
--the rest LVM

At this point, I'm guessing that the lost data is in the LVM part. When I boot, it says that there are two logical partitions in VolGroup00. So what I need to know is

1. Can I still access it or is the partition deleted?
2. Can the data in the deleted partition be restored?
3. How can I restore the data in the partition? I read the data recovery article on the ubuntu website, but it's over 50GB of files, I don't know where to back it up.

Any help would be great - here's the output of df -h:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup00-LogVol00
                       78G  2.4G   76G   4% /
/dev/sda2             190M   19M  162M  11% /boot
tmpfs                 248M  1.1M  247M   1% /dev/shm

```

/etc/mtab:
```

/dev/mapper/VolGroup00-LogVol00 / ext3 rw 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/sda2 /boot ext3 rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
sunrpc /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0

```

---

### Post by dstew on 2008-05-26
It seems Fedora assembled a logical volume out of your two ext3 partitions. If you did not format the volume, the data may still be there. Can you boot an Ubuntu Live CD? If so, boot it, and do **sudo fdisk -l** on the command line and see if the two partitions are still detectable.

---

### Post by elashish on 2008-05-26
sudo fdisk -l
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1717    13791771    7  HPFS/NTFS
/dev/sda2            1718        1742      200812+  83  Linux
/dev/sda3            1743       12161    83690617+  8e  Linux LVM

```

It seems that the partition is gone - however, I ran testdisk on the drive and the files still seem to be present. Can I restore them without backing them up elsewhere?

---

### Post by dstew on 2008-05-26
I think using Testdisk you can re-assemble your old partition table and recover the files. Maybe you can even get the files off the LV. See if you can open the LV from the Live CD system.

---

