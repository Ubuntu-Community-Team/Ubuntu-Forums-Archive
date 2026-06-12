---
title: "Gparted/parted/libparted bug, anyone care to test?"
date: 2010-01-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-01-20
All of the details are here:

[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/510179](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/510179)

I encountered this during the pre-alpha 2 iso testing but Colin Watson pointed out that this was **unrelated** to the ubiquity bug mentioned in the release notes:

> Manual partitioning fails in the graphical installer due to a bug in ubiquity: you can select existing partitions to use as targets for installation, but you can neither create new partitions nor delete existing partitions. As a workaround, users can install using the alternate CDs. This issue will be resolved for Alpha 3. (506585, 507012) 

Anyway, I'd appreciate any testing/confirmation possible. Certainly, since it involves partitioning, it's a high risk venture though!

As with any re-partitioning, and especially since we know this doesn't work right, a full backup of everything is imperative.

---

### Post by ranch hand on 2010-01-20
I will give it a whack a little later (this enening).  I have the A2 CD (from late the 14th).

I also have a single sata external enclosure that has nothing but a 8.04.3 on it.  It can go.

I plan to put the 8.04.4 on there to test upgrading to 10.04 so there is no problem.

---

### Post by kansasnoob on 2010-01-20
> **ranch hand said:**
> I will give it a whack a little later (this enening).  I have the A2 CD (from late the 14th).

I also have a single sata external enclosure that has nothing but a 8.04.3 on it.  It can go.

I plan to put the 8.04.4 on there to test upgrading to 10.04 so there is no problem.

re: 8.04.4, I don't know if they're going to do iso testing or not, but I installed 8.04 recently to do some testing for Ubuntuzilla and left it there for the same reason.

Someone has to be the guinea pig! Right after 8.04.4 is released it's time to try a Hardy > Lucid upgrade :D

Lucid is looking solid so far, I just want it to be great!!!!!!!!

---

### Post by ranch hand on 2010-01-20
OK.  Here is the problem.  I am not sure after reading the bug that you are working from the LiveCD or your installation.

So I fired up the LiveCD and deleted all partitions on the drive (4 + swap) with gparted.  Created a swap.  Closed gparted.

Opened installer.  Got to partitioner and could not create or delete a thing.  This is, I gather what the devs expect.

Fired up my test drive and came here to my daytime production OS.  Fired up gparted.  Created, one at a time, 2 ext3 partitions.  Created a swap partition.  Created 2 ext4 partitions at the same time.  Created a 3rd ext4 partition after that.

Had no trouble what so ever.

Now, I do not partition my drive right.  They have no primary partitions.  One big extended.  Therefore I did not delete the swap on there before doing these jobs.  I find that partitioning as one extended works great but you better have something on it or you may not be able to find it at all.  I bricked a couple of them before figuring that out.

I like them set up this way.  Total flexibility.  The problem is I do not know if this effects the operation of gparted in any way in relation to what you are attempting to find out.

---

### Post by mc4man on 2010-01-20
No problem here either - going with idea of what I think you did -  sandwiching ext4 and swaps and applying   all at same time ..?
(ext4, swap. ext4, swap. ext4

Though couldn't go up to 18 ld's  (10

---

### Post by kansasnoob on 2010-01-21
> I am not sure after reading the bug that you are working from the LiveCD or your installation.

The testing I did this AM was done on my installed Lucid, but the behavior is the same with Gparted from the Lucid Live CD.

> Fired up my test drive and came here to my daytime production OS. Fired up gparted. Created, one at a time, 2 ext3 partitions. Created a swap partition. Created 2 ext4 partitions at the same time. Created a 3rd ext4 partition after that.

Had no trouble what so ever.

And your production OS is Lucid?

---

### Post by kansasnoob on 2010-01-21
> **mc4man said:**
> No problem here either - going with idea of what I think you did -  sandwiching ext4 and swaps and applying   all at same time ..?
(ext4, swap. ext4, swap. ext4

Though couldn't go up to 18 ld's  (10

Maybe the number of partitions is part of the problem, but Gparted in both Jaunty and Karmic had no problem dealing with that.

I wonder what the maximum number of logical partitions in one extended partition is? I know I've gone over 20 before.

---

### Post by ranch hand on 2010-01-21
I have 2 production OS'.  One, where I am now is 9.04.  I ca ngo to bed and not get up with it frozen in the morning and boinc screwed.

Where I was doing the gparted stuff for this thread was my day time OS.  It is a 9.04>9.10>10.04 upgrade and is running very nicely.

I am getting to prefer it to this one quite a bit.

You were not trying to partition on the same drive you were mounted on were you?  That is not a good thing to do (I have been known to "label" partitions on the same drive as gparted but it makes me nervous).

gparted on the CD worked great as it did on my install.  The CD installer partitioner was a hopeless mess.

In theory there should be no limit to logical partitions.  In practice I have found that you can get errors in big numbers such as a tiny amount of overlap (due to the guy on the keyboard probably) that will eventually result in gparted refusing to make more partitions.   I think that particular problem is harder to get in the gparted version in 10.04 (it is caused by trying to be to exact in the volume of the new partition which may not line up on the drive right causing the next partition to overlap.

This version does not sak if it can "round" the sucker to the nearest correct point.  It just does it.

I believe that I peaked during the last testing with 28 partitions on one drive and room for a couple more.  I am being good this time and only have 13 on the bugger.

---

### Post by kansasnoob on 2010-01-21
I see someone exceeded 50 logical partitions:

[http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)

That's wild.

---

### Post by kansasnoob on 2010-01-21
One thing I noticed with all of this testing is the libparted version:

> Libparted 1.8.8.git-**dirty**

I don't think I've ever seen dirty before.

---

### Post by ranch hand on 2010-01-21
> **kansasnoob said:**
> One thing I noticed with all of this testing is the libparted version:



I don't think I've ever seen dirty before.

OH, I know that one.  It is very like saying "Lets go clean the barn and git dirty".

---

### Post by mc4man on 2010-01-21
Even though I can't possibly use - , it does seems number 17 is a no go for lucid

> Create Logical Partition #4 (ext2, 996.19 MiB) on /dev/sdb  00:00:14    ( ERROR )
     	
create empty partition  00:00:06    ( SUCCESS )
     	
path: /dev/sdb17
start: 65673783
end: 67713974
size: 2040192 (996.19 MiB)
set partition type on /dev/sdb17  00:00:07    ( SUCCESS )
     	
new partition type: ext2
create new ext2 file system  00:00:01    ( ERROR )
     	
mkfs.ext2 -L "" /dev/sdb17
     	
mke2fs 1.41.9 (22-Aug-2009)
Could not stat /dev/sdb17 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

Edit: though to some extent it does exist - just is an 'unknown' file type
And noting here it was the 13TH LD in an Extended ( 15 total on drive

---

### Post by ranch hand on 2010-01-21
My test platform is set up in a dual sata external enclosure.  Roughly sda is root partitions and sdb is home.

My current "production" OS - daytime is on sda17 and sdb15.

I will try making partitions for another installation tomorrow morning from here before I switch over to that drive.

Now I am hitting the hay.

---

### Post by seeker5528 on 2010-01-21
> **ranch hand said:**
> My current "production" OS - daytime is on sda17 and sdb15.

Interesting. Is sda17 on a PATA or SATA drive?

According to devices.txt included with the kernel source in the documentation directory, the older PATA IDE was allocated enough numbers for 63 partitions.

SCSI was only allocated enough numbers for 15 partitions.

Theoretically with SATA drivers being based on the SCSI driver and using the sdXXX numbering scheme, you should only be able to do 15 partitions on a SATA drive.

I have seen complaints from people in the past who had older PATA drivers, following the hdXXX numbering scheme for their drives, who lost access to their partitions with numbers higher than 15 when their kernel was upgraded to one that changed them from an older PATA driver to a newer PATA driver that was based on the SCSI drivers and their drives started showing as sdX instead of hdX. 

Don't know what is expected in distributions where newer PATA drivers based on the SCSI drivers are being used, but the distribution is set up to recognize those drives are PATA and use the hdXXX numbering scheme for them, I'm guessing if the hdXXX scheme is used you probably should be able to do 63 partitions.

Never had a reason to do more than 8 partitions on a single drive myself.

Maybe there is finally starting to be some effort to break the 15 partition per SCSI drive limit? If so it is not yet reflected in the documentation.

Later, Seeker

---

### Post by ranch hand on 2010-01-21
All right, I tried adding sda18 and sdb16 both as ext4.  sda18 failed to format.  sdb16 created and formated fine.  This was with gparted from the LiveCD.

Thinking that I had screwed the partitioning in some manner that limited the drive, which is getting full, I went back to my 9.04 install and tried formating the bugger from there.  No problem,slick,fast and easy.

So there is some kind of problem with this version of gparted that is on 10.04 and the LiveCD for it.

@seeker
This box is all SATA.  All of them 320Gb drives.  2 internal, 1 in an external enclosure, and 2 in a dual external enclosure.

The dual external is my test platform (on it now).  I do not like RAID so the bugger will only boot from the first drive in the enclosure.  Thus the root partitions on one and home on the other.

As you can see from my report above sda is now at sda18 (there is one OS on a single partition and a partition for testing "back in time" so there are 2 more on it than sdb).

My internal drives are now turned off in bios to prevent any possible contamination from the test OS'.

---

### Post by kansasnoob on 2010-01-21
One thing I'd point out here however is that Lucid's Gparted failed to resize the original sda6 when I was done playing:

[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/510179/comments/4](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/510179/comments/4)

Karmic's Gparted finished the job with no problems.

Has anyone else ever noticed that "dirty" associated with git? I assume that means something :confused:

---

### Post by ranch hand on 2010-01-21
> **kansasnoob said:**
> 
Has anyone else ever noticed that "dirty" associated with git? I assume that means something :confused:
I would like to know where you see this.

Checking in synaptic I do not find anything like that.

I have libparted1.8-10 (version) 1.8.8.git.2008.03.24-11.1ubuntu6
and libparted1.8-12 (version) 1.8.8.git.2009.07.19-5ubuntu1

---

### Post by kansasnoob on 2010-01-21
It's at the beginning of the "saved details" of every Gparted test in Lucid:

```
GParted 0.5.0

Libparted 1.8.8.git-dirty
Grow /dev/sda6 from 18.69 GiB to 34.36 GiB  00:00:59    ( ERROR )
     	
calibrate /dev/sda6  00:00:01    ( SUCCESS )
     	
path: /dev/sda6
start: 77095998
end: 116294534
size: 39198537 (18.69 GiB)
check file system on /dev/sda6 for errors and (if possible) fix them  00:00:52    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sda6
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

21522 inodes used (1.75%)
729 non-contiguous files (3.4%)
19 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 3471/232/0
2888335 blocks used (58.95%)
0 bad blocks
2 large files

18458 regular files
3013 directories
0 character device files
0 block device files
0 fifos
0 links
42 symbolic links (26 fast symbolic links)
0 sockets
--------
21513 files
e2fsck 1.41.9 (22-Aug-2009)
grow partition from 18.69 GiB to 34.36 GiB  00:00:03    ( SUCCESS )
     	
old start: 77095998
old end: 116294534
old size: 39198537 (18.69 GiB)
new start: 77095998
new end: 149147459
new size: 72051462 (34.36 GiB)
check file system on /dev/sda6 for errors and (if possible) fix them  00:00:02    ( ERROR )
     	
e2fsck -f -y -v /dev/sda6
     	

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

e2fsck 1.41.9 (22-Aug-2009)
e2fsck: No such file or directory while trying to open /dev/sda6
grow file system to fill the partition  00:00:01    ( ERROR )
     	
resize2fs /dev/sda6
     	
resize2fs 1.41.9 (22-Aug-2009)
open: No such file or directory while opening /dev/sda6
libparted messages    ( INFO )
     	
Error informing the kernel about modifications to partition /dev/sda6 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda6 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sda (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sda.

========================================

```

This is one from Karmic (on the same partition):

```
GParted 0.4.5

Libparted 1.8.8.1.159-1e0e
Check and repair file system (ext3) on /dev/sda6  00:01:17    ( SUCCESS )
     	
calibrate /dev/sda6  00:00:03    ( SUCCESS )
     	
path: /dev/sda6
start: 77095998
end: 149147459
size: 72051462 (34.36 GiB)
check file system on /dev/sda6 for errors and (if possible) fix them  00:01:03    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sda6
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

21522 inodes used (1.75%)
729 non-contiguous files (3.4%)
19 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 3471/232/0
2888335 blocks used (58.95%)
0 bad blocks
2 large files

18458 regular files
3013 directories
0 character device files
0 block device files
0 fifos
0 links
42 symbolic links (26 fast symbolic links)
0 sockets
--------
21513 files
e2fsck 1.41.9 (22-Aug-2009)
grow file system to fill the partition  00:00:11    ( SUCCESS )
     	
resize2fs /dev/sda6
     	
Resizing the filesystem on /dev/sda6 to 9006432 (4k) blocks.
The filesystem on /dev/sda6 is now 9006432 blocks long.

resize2fs 1.41.9 (22-Aug-2009)

========================================
```

---

### Post by kansasnoob on 2010-01-21
I was curious so I ran a chdsk from Lucid's Gparted that succeeded (something to do with the version#?):

```
GParted 0.5.0

Libparted 1.8.8.git-dirty
Check and repair file system (ext3) on /dev/sda12  00:00:21    ( SUCCESS )
     	
calibrate /dev/sda12  00:00:01    ( SUCCESS )
     	
path: /dev/sda12
start: 287081613
end: 312576704
size: 25495092 (12.16 GiB)
check file system on /dev/sda12 for errors and (if possible) fix them  00:00:19    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sda12
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

3568 inodes used (0.45%)
123 non-contiguous files (3.4%)
3 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 465/34/0
597169 blocks used (18.74%)
0 bad blocks
1 large file

2908 regular files
649 directories
0 character device files
0 block device files
0 fifos
0 links
2 symbolic links (2 fast symbolic links)
0 sockets
--------
3559 files
e2fsck 1.41.9 (22-Aug-2009)
grow file system to fill the partition  00:00:01    ( SUCCESS )
     	
resize2fs /dev/sda12
     	
resize2fs 1.41.9 (22-Aug-2009)
The filesystem is already 3186886 blocks long. Nothing to do!

========================================
```

---

### Post by mc4man on 2010-01-21
not terribly up on git but...
> A working tree is said to be "dirty" if it contains modifications which have not been committed to the current branch.

(did get it to do (& recognize) a /dev/sdx17 once (happened to be a fat32.

After deleting and retrying would not do successfully again

Edit: 
in regards to post 14 - I remember reading that in the past though the # for sata (sdx) was slightly different
for ide (hdx - 63, 4 reserved - 59 ld's
for sata - 17 ( if also 4 resv., then 13 ld's ( failing here on the 13th ld (sdb17

---

### Post by ranch hand on 2010-01-21
Beats me.  I can't find on my search engine.

---

### Post by kansasnoob on 2010-01-21
> A working tree is said to be "dirty" if it contains modifications which have not been committed to the current branch. 

I was sure it was some sort of development term.

Just regarding this, and bug filing on a dev release in general, I used to think, "ah, it's still in heavy development so there's no point in filing a bug report on this", but I've since changed my mind.

If something just doesn't work right and if you can duplicate the error then file a bug, eh? Then be nice and follow up on it.

I try and review my old bug reports from time to time and if it's been fixed, but I don't know when or how, or if I later find I was the cause then I try to make sure and mark them invalid. If there's no useful info for anyone else then I also mark them private so they're not clogging up the works.

---

