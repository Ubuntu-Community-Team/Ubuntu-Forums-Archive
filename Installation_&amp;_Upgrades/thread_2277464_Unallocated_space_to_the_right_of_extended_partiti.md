---
title: "Unallocated space to the right of extended partition, but can't grow extended"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by gammmae105 on 2015-05-09
I installed ubuntu alongside my windows partition, so now I can boot any OS through grub. 

However, when I initially installed Ubuntu, I allocated less than desired, and would like to have more space in my extended partition (or ext4??)

But when I try to move/resize the extended partition (light blue) into the unallocated space to the right, it throws an error (something about constraints not being satistfied). I cannot grow the ext4 (dark blue), as it seems to be at max capacity already (possibly since the unallocated space is outside the extended partition). Also, extra information: the error does not say anything about overlap.

Here's a picture of the partitions window: 
[ATTACH=CONFIG]261846[/ATTACH].

And here's a picture of the error:
[ATTACH=CONFIG]261847[/ATTACH]


My question is, how can I safely make the 244.14GB partition have more space?
I want to add the unallocated space, but it keeps giving me an error no matter how much of the unallocated space I resize the extended partition into.

Thanks in advance for the help!

---

### Post by ajgreeny on 2015-05-09
You will have to run gparted in Ubuntu from a live USB/DVD; you can not work on any ubuntu partitions using gparted installed in the OS you are trying to work on.

If this does not help explain the difficulties you are having it is probably because some of the ubuntu partitions are mounted, so right click on any of them in gparted and choose **unmount** if it is an available option.  You should then be able to enlarge the extended sdb3 partition, and then extend the  the sdb5 partition into the unallocated space within sdb3.

---

### Post by gammmae105 on 2015-05-09
> **ajgreeny said:**
> You will have to run gparted in Ubuntu from a live USB/DVD; you can not work on any ubuntu partitions using gparted installed in the OS you are trying to work on.

If this does not help explain the difficulties you are having it is probably because some of the ubuntu partitions are mounted, so right click on any of them in gparted and choose **unmount** if it is an available option.  You should then be able to enlarge the extended sdb3 partition, and then extend the  the sdb5 partition into the unallocated space within sdb3.

I was already running from a live USB, and the devices were all unmounted to begin with when I got those errors. Still am not able to enlarge the sdb3 partition at all by any amount (not even +1GB)

---

### Post by oldfred on 2015-05-09
You have to expand extended first. 
What exactly were the errors or constraints it posted? That may give a clue on what to fix.

I might just run fsck on the ext4 partition, just to be sure that is not an issue.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb5
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb5

---

### Post by gammmae105 on 2015-05-09
> **oldfred said:**
> You have to expand extended first. 
What exactly were the errors or constraints it posted? That may give a clue on what to fix.

I might just run fsck on the ext4 partition, just to be sure that is not an issue.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb5
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb5

The extended is unable to be expanded. The only error/additional information shown was that it couldnt satisfy the constraints, nothing else at all, which is why I was confused.

Also, doing those 2 commands you listed on both the sdb5 (ext4) and the parent extended partition (sdb3) results in this, errors of interest are bolded (happens for sdb3 parent(?) partition -- the extended partition which houses the sdb5):

```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb5
                                                                                
      337198 inodes used (2.11%, out of 16007168)
        1064 non-contiguous files (0.3%)
         350 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 288507/56
     5471112 blocks used (8.55%, out of 63999744)
           0 bad blocks
           1 large file

      235406 regular files
       36498 directories
          57 character device files
          25 block device files
           1 fifo
          16 links
       65201 symbolic links (48543 fast symbolic links)
           1 socket
------------
      337205 files
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sdb5
e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      337198 inodes used (2.11%, out of 16007168)
        1064 non-contiguous files (0.3%)
         350 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 288507/56
     5471112 blocks used (8.55%, out of 63999744)
           0 bad blocks
           1 large file

      235406 regular files
       36498 directories
          57 character device files
          25 block device files
           1 fifo
          16 links
       65201 symbolic links (48543 fast symbolic links)
           1 socket
------------
      337205 files
[B]ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb3
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb3
Could this be a zero-length partition?
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sdb3
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb3
Could this be a zero-length partition?[/B]
```

---

### Post by yancek on 2015-05-09
sdb3 is your Extended partition and doesn't contain a filesystem so there is no point in running a filesystem check.  How about just creating another primary partition out of the unallocated space as you are only using 3 at present.  Use it for data or /home.  Not sure why you are unable to extended the Extended partition, seems pretty odd.

---

### Post by tim105 on 2015-05-12
Right-click your Extended partition, remove "lba" flag, then extend to the right. 

Remember to use Gparted from live CD and unmount the partition/s on the disk that you will be working on.  Place lba flag again when you're done.

---

