---
title: "Hardy amd64 Live CD gparted annoyance"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by robeast on 2008-04-26
Hey, I'm trying to resize my Gutsy partition to make room for Hardy. When I run the move/resize operation it gets through performing the file system check fine then moves on to a resize attempt. When it tries to resize it says that it needs to run e2fsck first 	:roll: After it checks again, gparted thinks that the partition is already the size I want it to be. BUNK! Any ideas?

Here's the details file:

```
Move /dev/sdb1 to the left and shrink it from 54.89 GiB to 28.21 GiB  06:33    ( ERROR )
     	
calibrate /dev/sdb1  00:00    ( SUCCES )
     	
path: /dev/sdb1
start: 63
end: 115105724
size: 115105662 (54.89 GiB)
calculate new size and position of /dev/sdb1  00:00    ( SUCCES )
     	
requested start: 0
requested end: 59167394
requested size: 59167395 (28.21 GiB)
new start: 63
new end: 59167394
new size: 59167332 (28.21 GiB)
check filesystem on /dev/sdb1 for errors and (if possible) fix them  03:10    ( SUCCES )
     	
e2fsck -f -y -v /dev/sdb1
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

255034 inodes used (3.54%)
7363 non-contiguous inodes (2.9%)
# of inodes with ind/dind/tind blocks: 16453/298/0
5347576 blocks used (37.17%)
0 bad blocks
1 large file

199523 regular files
25623 directories
132 character device files
26 block device files
2 fifos
480 links
29701 symbolic links (23239 fast symbolic links)
18 sockets
--------
255505 files
e2fsck 1.40.8 (13-Mar-2008)
shrink filesystem  00:01    ( ERROR )
     	
resize2fs /dev/sdb1 29583665K
     	
resize2fs 1.40.8 (13-Mar-2008)
Please run 'e2fsck -f /dev/sdb1' first.

check filesystem on /dev/sdb1 for errors and (if possible) fix them  03:20    ( SUCCES )
     	
e2fsck -f -y -v /dev/sdb1
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

255034 inodes used (3.54%)
7363 non-contiguous inodes (2.9%)
# of inodes with ind/dind/tind blocks: 16453/298/0
5347576 blocks used (37.17%)
0 bad blocks
1 large file

199523 regular files
25623 directories
132 character device files
26 block device files
2 fifos
480 links
29701 symbolic links (23239 fast symbolic links)
18 sockets
--------
255505 files
e2fsck 1.40.8 (13-Mar-2008)
grow filesystem to fill the partition  00:02    ( SUCCES )
     	
resize2fs /dev/sdb1
     	
resize2fs 1.40.8 (13-Mar-2008)
The filesystem is already 14388207 blocks long. Nothing to do!
```

---

### Post by hotdoog on 2008-05-20
this is the exact same problem I am having in hardy64, but it's not the live cd!

no solutions? Maybe I'll try it from root rather than gksudo?:confused:

---

### Post by hotdoog on 2008-05-20
Yep, it seems that running as root did the trick:

From console:

```
$ sudo -s -H
# gparted
```

That's it!:guitar:

---

