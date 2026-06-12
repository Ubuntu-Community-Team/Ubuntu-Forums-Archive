---
title: "Upgrading to 8.1, reformatting boot partition"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by kentcb on 2008-10-10
Hi people,

I'm wanting to upgrade to 8.1 as per the instructions [here]("http://www.ubuntu-unleashed.com/2008/10/upgrade-from-hardy-heron-to-ubuntu.html"). However, before I do I need to confirm something.

I want to also change my boot partition to jfs (it's currently ext3). I don't quite understand linux partitioning yet, but I'm pretty sure I have separate boot and home partitions. System monitor reports:

Device = /dev/sda1, Directory = /
Device = /dev/sda2, Directory = /home

I think that means I should be able to download 8.1 and re-install it on /dev/sda1 after formatting as jfs. Can anyone confirm?

Thanks,
Kent

---

### Post by WWSmith36 on 2008-10-10
Let´s make sure of your configuration first, so please post the output of

```
sudo fdisk -lu
df -h
```

---

### Post by kentcb on 2008-10-10
Here you go:

```
kent@raph:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    93755339    46877638+  83  Linux
/dev/sda2        93755340   101562929     3903795   82  Linux swap / Solaris
/dev/sda3       101562930   312576704   105506887+  83  Linux
kent@raph:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              45G  3.3G   39G   8% /
varrun                501M  160K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   44K  501M   1% /dev
devshm                501M   12K  501M   1% /dev/shm
lrm                   501M   39M  463M   8% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3             100G   37G   59G  39% /home
gvfs-fuse-daemon       45G  3.3G   39G   8% /home/kent/.gvfs
kent@raph:~$ 

```
Cheers,
Kent

---

### Post by WWSmith36 on 2008-10-10
> I don't quite understand linux partitioning yet, but I'm pretty sure I have separate boot and home partitions

It looks like you don´t have a separate boot partition.  You boot partition is under root on sda1.

Confirmed.  You can download and re-install on /dev/sda1.  During the installer you can choose to format as jfs.  The most important thing is that do not format sda2 during the installer.  You can have it mount it as /home but do not touch it in any other way  That way all you data and settings will be preserved.

---

