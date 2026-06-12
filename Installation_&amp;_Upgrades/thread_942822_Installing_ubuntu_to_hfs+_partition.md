---
title: "Installing ubuntu to hfs+ partition"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by yazemu on 2008-10-09
Hello, I'm trying to start a fresh install of ubuntu. My plan is to mount / to an ext2 partition and then /home and /usr directories to an hfs+ partition. Now I know that Ubuntu cannot write to a journaled hfs+ filesystem, but it can write to one that isn't journaled. So I formatted my hard disk using the mkfs.hfsplus command
```
root@ubuntu:/home/ubuntu# mkfs.hfsplus -s /dev/sda3
Initialized /dev/sda3 as a 219 GB HFS Plus volume

```
When I get to the partitioning part of the ubuntu installer, it recognizes the partition I just made as hfsx. I'm glad that it recognizes it, but it wont allow me to use it as a mount point unless I format it with a different file system.

Is there a way to get the installer to mount on this partition anyways?
or perhaps manually install ubuntu to work for this?

If all else fails I suppose I could try installing everything to my ext2 partition and then change the mount points afterwards. Do you think this work?

---

### Post by Ptero-4 on 2008-11-02
Linux can't be installed on a windows or macos partition. It can use any of this partitions for storage (read-write both formats) though.

---

