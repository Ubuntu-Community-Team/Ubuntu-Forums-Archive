---
title: "how best to remove MS Windows?"
date: 2019-05-03
forum: Installation &amp; Upgrades
---

### Post by dwater on 2019-05-03
Updating Windows (10-64) has screwed my dual boot setup once too often, so having escaped from the latest incarnation of the the problems, I'm looking to wipe MS Windows completely...

What's the best way for doing this? Ideally, I'd like the disk space used by Windows to be assimilated into the disk space I have available in ~:

$ df -h ~
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p6   67G   58G  5.8G  91% /

Any recommendations?

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.2 LTS"

---

### Post by TheFu on 2019-05-03
If you want to wipe all Windows files, delete the partitions where those are located.

There isn't an easy answer for how to make use of that space going forward. It depends on where things are in the storage layout which makes the most sense and if you use simple partitions, LVM, ZFS, BRTFS, and/or any encryption.

Personally, I wouldn't allow / to be larger than 25G and I'd use LVM.  I've posted my "ideal" setup in these forums a few times. But if you are really new to Linux, some of this stuff is dangerous.

Before changing any partitions in any way, always, always, always have know-you-can-restore backups.  It is very easy to completely wipe an OS while modifying partitions. People show up here every week after they'd done that, accidentally. Backups. Backups, backups.

---

### Post by jglen4902 on 2019-05-04
A partition editor will allow you reclaim the Windows space and format that space to a Linux filesystem such ext4 or BTRFS and to set up a good partitioning scheme.  You could use that new space as a /data partition or extend your /home with a /home/multimedia, or something else that you might think of.  Then just make sure your new partition(s) show up in /etc/fstab, and press on with Linux happiness.

---

