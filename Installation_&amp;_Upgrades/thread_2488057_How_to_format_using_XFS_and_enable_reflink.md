---
title: "How to format using XFS and enable reflink?"
date: 2023-06-21
forum: Installation &amp; Upgrades
---

### Post by edflecko on 2023-06-21
Using Ubuntu 22.04, do I need to format a drive using a command like:

sudo mkfs.xfs -b size=4096 -m reflink=1,crc=1 /dev/sdb

or is reflink enabled by default in Ubuntu 22.04? Is there a way to find out if reflink is already enabled on a drive that has already been formatted? 



Ed

---

### Post by TheFu on 2023-06-21
NEVER format an entire disk with a file system. Always create a partition table and a partition to hold a file system, assuming you don't want to use a volume manager.  
The typical way would be to use mkfs:
```
              sudo mkfs -t xfs /dev/sdb1
```

According to the manpage, 
```
                   reflink=value
                          This option enables the use of a separate  reference  count  btree
                          index  in  each allocation group. The value is either 0 to disable
                          the feature, or 1 to create a reference count btree in each  allo&#8208;
                          cation group.

                          The  reference count btree enables the sharing of physical extents
                          between the data forks of different files, which is commonly known
                          as  "reflink".   Unlike  traditional Unix filesystems which assume
                          that every inode and logical block pair map to a  unique  physical
                          block, a reflink-capable XFS filesystem removes the uniqueness re&#8208;
                          quirement, allowing up to  four  billion  arbitrary  inode/logical
                          block  pairs  to  map  to a physical block.  If a program tries to
                          write to a multiply-referenced block in a file, the write will  be
                          redirected  to  a  new  block, and that file's logical-to-physical
                          mapping will be changed to the new block ("copy on write").   This
                          feature  enables the creation of per-file snapshots and deduplica&#8208;
                          tion.  It is only available for the data forks of regular files.

                          [B]By default, mkfs.xfs will create reference count btrees and there&#8208;
                          fore will enable the reflink feature.[/B]  This feature is only avail&#8208;
                          able for filesystems created with the (default)  -m  crc=1  option
                          set.  When  the option -m crc=0 is used, the reference count btree
                          feature is [B]not supported and reflink is disabled.
[/B]
                          Note: the filesystem DAX mount option ( -o dax )  is  incompatible
                          with  reflink-enabled XFS filesystems.  To use filesystem DAX with
                          XFS, specify the -m reflink=0 option to mkfs.xfs  to  disable  the
                          reflink feature.
```
check your local manpage, since you may have a different version of XFS on your system than I have on mine. YMMV.

On my system, I'd use the first command above, if I wanted reflinks and xfs.  Because I use LVM and ext4 integrates with LVM better, I'd use ext4 on Ubuntu systems.

---

