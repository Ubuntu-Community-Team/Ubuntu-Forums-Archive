---
title: "Expand size of ubuntu partition"
date: 2013-09-24
forum: Installation &amp; Upgrades
---

### Post by therealsam on 2013-09-24
As the title suggests I am running out of space on my main partition and want to expand it.
Here's the image of my current disk [IMG]http://i.imgur.com/H6EqxUrh.png[/IMG]


There are two things I need to do:
1) Move /dev/sda7(swap space) to the end so as to accomodate /dev/sda5 as a part of my ubuntu partition(do i need to format it to ext4? ).
2) use some of the space from /dev/sda3 i.e. move the ubuntu partition backwards.

All of the tutorials I saw over the internet involved expansion towards( including ubuntu docs) the right end of the disk and none towards the left.
Link to any tutorial is fine.
Thank you.

---

### Post by TheFu on 2013-09-24
The image didn't display for me.
I won't let facts get in the way of posting a solution.

You can use clonezilla or fsarchive to backup your installation 100%. The backups will be compressed, so about 50% smaller.  fsarchive can restore a partition to any new partition with enough storage to hold it - larger partitions are fine too.

If you will post the output of **sudo parted -l**, then we can make suggestions.  Most likely, the easy answer will be to use gparted to shift stuff to the right, but if there is an extended partition involved, that becomes more complex.

BTW, I'd only make / 20G in size, never larger.  Then I'd add partitions for other needs as necessary.  /home is commonly a different partition, but almost any directory can be on a different partition ... which will free up /.  Does that make sense?  For example, create a new partition anywhere and put /usr or /var  inside it.  those tend to be the larger file systems on desktop Linux outside /home.

I hope this is clear?

---

### Post by therealsam on 2013-09-25
here's the output of [B]sudo parted -l
[/B]Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  98.7MB  98.7MB  primary   fat16        diag
 2      98.7MB  53.8GB  53.7GB  primary   ntfs
 3      53.8GB  199GB   145GB   primary   ntfs
 4      199GB   250GB   51.0GB  extended               lba          ---> this is /dev/sda3
 6      199GB   216GB   16.7GB  logical   ext4                        ---> this is my linux partition
 7      216GB   218GB   2136MB  logical                                ---> this is swap memory /dev/sda7
 5      218GB   250GB   32.2GB  logical   ntfs                         ---> this is /dev/sda5


Also do I need to reformat my drive(/dev/sda5) to ext4 as i have found a work around to this by editing the /etc/fstab file
and adding this at the end 
**UUID=(Your HardDrive UUID) /media/user/(YOUR UUID) ntfs-3g defaults,uid=1000,gid=1000,dmask=000,fmask=000 0 0**

Although I am not sure regarding what it does but it works.

---

