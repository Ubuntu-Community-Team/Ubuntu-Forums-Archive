---
title: "[SOLVED] help repartitioning for more disk space"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by nhasian on 2008-05-05
Hello,

originally when i installed Ubuntu 8.04 hardy heron on my second internal hard disk (i have windows vista on my primary hard disk) I used the manual settings in the partition manager during the install to resize my NTFS partition and allocate 10 gigs to the swap and ext3 partitions.  Originally my thinking was that windows and linux could share the data and workspace on the NTFS drive.  I've run into some hiccups trying to use the NTFS partition in linux, so I've decided I want to get rid of it altogether and just make it all ext3.

So my question is, how can i remove the ntfs parition from my secondary hard disk and replace it with ext3?  I'm not sure what tool or program to use, and if I should just create a new ext3 partition, or somehow just resize my existing ext3 partition to reclaim the space that was NTFS?

Please advise.  Thanks in advance!

---

### Post by bsh on 2008-05-05
go to your synaptic package manager and install gparted - that's the partition manager used on the live cd. with that, you can just:
- delete your ntfs partition and make a new one, formatted to ext3 (this will obviously destroy all data on the partition)
or
- format the existing ntfs partition (without deleting it) to ext3 (this will obviously destroy all data on the partition)
or
- you can use command line tools like mkfs to make a new ext3 filesystem

alternatively, put back your live cd and boot from it, so you can use gparted, but then you might have to manually edit /etc/fstab.

---

### Post by az on 2008-05-05
You can boot the live cd, use gparted (partition editor in System, Administration) to delete the ntfs partition and then resize the existing ext3 partition to use the rest of the space.  Just grab the arrow on the left of the ext3 partition and drag it to the left to use all the freed-up space.

---

### Post by n6yga on 2008-05-05
Just remember that when using gParted, things will go very slowly!

It took about 8 hours yesterday to grow a ext3 partition from 21gigs to 46gigs.

Yikes!

Mark.

---

### Post by nhasian on 2008-05-05
Thanks for your help.  I was able to install gpart, delete the ntfs partition, unmount, move and remount the swap partition but i had to boot to the liveCD to resize the ext3 partition.  It seemed to all work okay except i ran into a glitch at the end.  now when i run gpart and look at /sdb3 it shows there is 15 gigs of unused space at the end of the disk, which is exactly where my original ext3 partition was.  I saved the details from gpart hoping i could get some help.  I think its at the end where it says "grow filesystem to fill the partition":

GParted 0.3.5

Libparted 1.7.1

Grow /dev/sdb3 from 17.67 GiB to 110.84 GiB  21:55    ( ERROR )
     	
calibrate /dev/sdb3  00:00    ( SUCCES )
     	
path: /dev/sdb3
start: 197374590
end: 234436544
size: 37061955 (17.67 GiB)
calculate new size and position of /dev/sdb3  00:00    ( SUCCES )
     	
requested start: 1992060
requested end: 234436544
requested size: 232444485 (110.84 GiB)
new start: 1992060
new end: 234436544
new size: 232444485 (110.84 GiB)
check filesystem on /dev/sdb3 for errors and (if possible) fix them  00:48    ( SUCCES )
     	
e2fsck -f -y -v /dev/sdb3
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

115785 inodes used (9.99%)
553 non-contiguous inodes (0.5%)
# of inodes with ind/dind/tind blocks: 5247/43/0
682526 blocks used (14.73%)
0 bad blocks
1 large file

86712 regular files
12243 directories
69 character device files
26 block device files
2 fifos
0 links
16717 symbolic links (15883 fast symbolic links)
7 sockets
--------
115776 files
e2fsck 1.40.8 (13-Mar-2008)
move partition to the left  00:00    ( SUCCES )
     	
old start: 197374590
old end: 234436544
old size: 37061955 (17.67 GiB)
new start: 1992060
new end: 39054014
new size: 37061955 (17.67 GiB)
move filesystem to the left  19:05    ( SUCCES )
     	
using internal algorithm
copy 37061955 sectors
finding optimal blocksize
     	
copy 32768 sectors using a blocksize of 64 sectors  00:03    ( SUCCES )
     	
32768 of 32768 copied
2.71883 seconds
copy 32768 sectors using a blocksize of 128 sectors  00:02    ( SUCCES )
     	
32768 of 32768 copied
2.69637 seconds
copy 32768 sectors using a blocksize of 256 sectors  00:03    ( SUCCES )
     	
32768 of 32768 copied
2.46464 seconds
copy 32768 sectors using a blocksize of 512 sectors  00:02    ( SUCCES )
     	
32768 of 32768 copied
2.16983 seconds
copy 32768 sectors using a blocksize of 1024 sectors  00:02    ( SUCCES )
     	
32768 of 32768 copied
2.13874 seconds
copy 32768 sectors using a blocksize of 2048 sectors  00:01    ( SUCCES )
     	
32768 of 32768 copied
1.47441 seconds
copy 32768 sectors using a blocksize of 4096 sectors  00:02    ( SUCCES )
     	
32768 of 32768 copied
1.15188 seconds
copy 32768 sectors using a blocksize of 8192 sectors  00:01    ( SUCCES )
     	
32768 of 32768 copied
0.952341 seconds
copy 32768 sectors using a blocksize of 16384 sectors  00:00    ( SUCCES )
     	
32768 of 32768 copied
0.865629 seconds
optimal blocksize is 16384 sectors (8.00 MiB)
copy 36767043 sectors using a blocksize of 16384 sectors  18:49    ( SUCCES )
     	
36767043 of 36767043 copied
37061955 sectors copied
check filesystem on /dev/sdb3 for errors and (if possible) fix them  00:41    ( SUCCES )
     	
e2fsck -f -y -v /dev/sdb3
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

115785 inodes used (9.99%)
553 non-contiguous inodes (0.5%)
# of inodes with ind/dind/tind blocks: 5247/43/0
682526 blocks used (14.73%)
0 bad blocks
1 large file

86712 regular files
12243 directories
69 character device files
26 block device files
2 fifos
0 links
16717 symbolic links (15883 fast symbolic links)
7 sockets
--------
115776 files
e2fsck 1.40.8 (13-Mar-2008)
grow filesystem to fill the partition  00:00    ( SUCCES )
     	
resize2fs /dev/sdb3
     	
resize2fs 1.40.8 (13-Mar-2008)
The filesystem is already 4632744 blocks long. Nothing to do!

calculate new size and position of /dev/sdb3  00:00    ( SUCCES )
     	
requested start: 1992060
requested end: 234436544
requested size: 232444485 (110.84 GiB)
new start: 1992060
new end: 234436544
new size: 232444485 (110.84 GiB)
check filesystem on /dev/sdb3 for errors and (if possible) fix them  00:40    ( SUCCES )
     	
e2fsck -f -y -v /dev/sdb3
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

115785 inodes used (9.99%)
553 non-contiguous inodes (0.5%)
# of inodes with ind/dind/tind blocks: 5247/43/0
682526 blocks used (14.73%)
0 bad blocks
1 large file

86712 regular files
12243 directories
69 character device files
26 block device files
2 fifos
0 links
16717 symbolic links (15883 fast symbolic links)
7 sockets
--------
115776 files
e2fsck 1.40.8 (13-Mar-2008)
grow partition from 17.67 GiB to 110.84 GiB  00:00    ( SUCCES )
     	
old start: 1992060
old end: 39054014
old size: 37061955 (17.67 GiB)
new start: 1992060
new end: 234436544
new size: 232444485 (110.84 GiB)
check filesystem on /dev/sdb3 for errors and (if possible) fix them  00:41    ( SUCCES )
     	
e2fsck -f -y -v /dev/sdb3
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

115785 inodes used (9.99%)
553 non-contiguous inodes (0.5%)
# of inodes with ind/dind/tind blocks: 5247/43/0
682526 blocks used (14.73%)
0 bad blocks
1 large file

86712 regular files
12243 directories
69 character device files
26 block device files
2 fifos
0 links
16717 symbolic links (15883 fast symbolic links)
7 sockets
--------
115776 files
e2fsck 1.40.8 (13-Mar-2008)
grow filesystem to fill the partition  00:00    ( ERROR )
     	
resize2fs /dev/sdb3
     	
resize2fs 1.40.8 (13-Mar-2008)
Please run 'e2fsck -f /dev/sdb3' first.


========================================



> **az said:**
> You can boot the live cd, use gparted (partition editor in System, Administration) to delete the ntfs partition and then resize the existing ext3 partition to use the rest of the space.  Just grab the arrow on the left of the ext3 partition and drag it to the left to use all the freed-up space.

---

### Post by fixitdude on 2008-05-05
Another great program is Parted Magic. It's a GUI based program, free, and it's on a bootable CD. It's got other tools on it as well, nice tool to have around.

[http://partedmagic.com](http://partedmagic.com)

---

### Post by nhasian on 2008-05-05
in case anyone else has a similar problem, i have found the solution.  it seems that the used and unused disk space was being misreported.  i booted off the live cd and ran gpart again.  first I minimized the ext3 partition as small as it would allow me to go and applied the changes.  then i maximized it as far as it would go and applied the changes again and now it fills the entire disc and i'm not missing any disk space.

---

