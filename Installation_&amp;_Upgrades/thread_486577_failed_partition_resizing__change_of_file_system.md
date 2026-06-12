---
title: "failed partition resizing / change of file system"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by rafalr on 2007-06-28
I have a separate partition for /, for /usr and for /home (and naturally swap). All apart from swap are ReiserFS. I (did) run Ubuntu Dapper. Now I have upgraded to Edgy and am in process of upgrading to 7.04 (just pulling new filles from the net).

As my /home was running short on space, while /usr had way too much space allocated, I decided to shrink  /usr from ca 20 GB to 6,4 GB and use the space to enlarge /home (now around 80 GB).

I launched a Live CD with Dapper and using GParted I did the following steps:
- marked /usr to be shrinked (resized) to 6,4 GB (at present only ca. 2,3 GB is used)
- was not able to resize (enlarge) /home inspite of free&unallocated space (most possibly because /home was the last partition on HD)
- then decided to use the freed space as a separate partition for multimedia data storage
- therefore decided to format this as XFS for better handling big files.

The job has been divided into two steps by GParted:
- resize /usr from 20 GB to 6,4 GB
- format new space/partition - ca 13,6 GB.

This has been applied but while GParted was running I went off to make a cup of ubuntu coffee and when was back the GParted window was closed - apparently at some stage (1 or 2 as above, no idea which) GParted aborted the job.

The situation I have now (when booting normally from HDD, as well as using othed Live CDs: 6.10, 7.04, Knoppix, Suse 10.1) I can see the following situation:
- the size of /usr is unchanged (around 20 GB)
- there is no separate (unallocated) space visible of around 13,6 GB - BUT
- the /usr partiton now shows that it is not 2,3 GB used as before, but 2,3+13,6 = 15,9 GB
- while ispection via nautilus, Gnome-commander or alike shows that the volume of the files stored on /usr remains still 2,3 GB

Apparently the part of the /usr partition that was supposed to be freed and formatted as XFS is now still ReiserFS (or "hidden" as part of /usr) but visible as used space.

How can I correct that ?
By the way, while approaching this matter I will be (hopefully) running 7.04, not 6.06.

rafal

here goes the output from fsck:

ubuntu@ubuntu:~$ fsck -r -t reiserfs /usr
fsck 1.40-WIP (14-Nov-2006)
reiserfsck 3.6.19 (2003 [www.namesys.com](www.namesys.com))

Will read-only check consistency of the filesystem on /usr
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes
bread: Cannot read the block (2): (Invalid argument).
reiserfs_open: bread failed reading block 2
bread: Cannot read the block (16): (Invalid argument).
reiserfs_open: bread failed reading block 16

reiserfs_open: the reiserfs superblock cannot be found on /usr.
Failed to open the filesystem.

If the partition table has not been changed, and the partition is
valid  and  it really  contains  a reiserfs  partition,  then the
superblock  is corrupted and you need to run this utility with
--rebuild-sb.

ubuntu@ubuntu:~$ 

any ideas now ?

---

