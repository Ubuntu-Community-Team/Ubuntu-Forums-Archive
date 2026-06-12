---
title: "bus error partitioning ubuntu 9.10"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by allaserik on 2010-02-01
Hi.

Trying to run on Satellite M45 - S269

Had Windows XP on it. Made backups and was hoping ubuntu would format and partition it.



I get following error (see below) when trying to make partitions. Hope you guys can help.

---------------------------------

GParted 0.4.5

Libparted 1.8.8.1.159-1e0e
Create Primary Partition #1 (ext4, 10.09 GiB) on /dev/sda  00:00:08    ( ERROR )
         
create empty partition  00:00:01    ( SUCCESS )
         
path: /dev/sda1
start: 63
end: 21157604
size: 21157542 (10.09 GiB)
set partition type on /dev/sda1  00:00:01    ( SUCCESS )
         
new partition type: ext4
create new ext4 file system  00:00:06    ( ERROR )
         
mkfs.ext4 -j -O extent -L "ubuntu" /dev/sda1
         
Filesystem label=ubuntu
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
662256 inodes, 2644692 blocks
132234 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2709520384
81 block groups
32768 blocks per group, 32768 fragments per group
8176 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done
mke2fs 1.41.9 (22-Aug-2009)
Bus error (core dumped)

========================================
Create Primary Partition #2 (ext4, 285.16 GiB) on /dev/sda

========================================

---

