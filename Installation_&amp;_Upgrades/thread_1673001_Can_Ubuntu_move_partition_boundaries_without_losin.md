---
title: "Can Ubuntu move partition boundaries without losing data within them?"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by bamim2 on 2011-01-21
[SIZE=2]I just installed Ubuntu 10.10 64 bit. I booted to the DVD & sliced up my 1TB hard drive. I had a 250GB unallocated space at the beginning of the drive & the rest of the drive was all one partition. I used Ubuntu to slice up the unallocated partition because the installation program didn't recognize the unallocated space as a slice it could install to. I then sliced up an  80GB partition of the 250GB partition & left the remaining 150GB as unallocated. 

I went back into the installation program & it recognized the 80GB slice, but for some reason it couldn't use about 8.7GB of that slice. I installed Ubuntu to the 71.3GB slice[/SIZE][SIZE=2] & now I see that it grabbed all of the extra 150GB that was unallocated & made one big partition out of it. [/SIZE][SIZE=2]I appears that Ubuntu has used the 8.7GB slice to put the lost-found into. 

Does Ubuntu have the ability to move the partition boundary without losing data inside that partition? If so, how do I do it?
[/SIZE]

---

### Post by jroa on 2011-01-21
How did you partition the drive?  Did you use GParted, fdisk, or some other program?

---

### Post by oldfred on 2011-01-21
I do not like to move the start of boot partitions, but you can shrink or expand to/from the right. Of course any partition changes means you should have good backups as we have been know to hit the wrong key.:)

Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

If you have created a separate /home your / (root) partition only needs to be 10 to 20GB.

---

### Post by bamim2 on 2011-01-23
[SIZE=2]Thank you, actually I saw your reply right away. There are lots of things to read here & I know better than to just rush right into this type of thing without doing my homework. On the bright side (for me), at least this is a brand new installation & if I do hose things up, hopefully I won't be losing much. Although since the installation grabbed more than I was hoping for, it's now touching the slice where I keep my virtual machines. 

It just dawned on me that there may be another way to do this. If I booted to the Ubuntu 10.10 installation DVD, would I be able to move that partition around more easily & less dangerously since it would then NOT be mounted as my boot partition?

[/SIZE]

---

### Post by kansasnoob on 2011-01-23
> It just dawned on me that there may be another way to do this. If I booted to the Ubuntu 10.10 installation DVD, would I be able to move that partition around more easily & less dangerously since it would then NOT be mounted as my boot partition?

I use Gparted from an Ubuntu (or other) Live CD to do a lot of partitioning with hardly any problems.

The one type of partition I almost never use Gparted to resize and/or move is Vista or Win7 OS partitions!

It's sort of hard to visualize what your current partitioning arrangement is, would you please post the output of:

```
sudo parted -l
```

BTW that's a lower case L at the end. Also, it's much easier to read if you wrap the text in code tags by using the # at the top of the reply box :)

---

### Post by bamim2 on 2011-01-23
Thanks. Here's the output you asked for:

Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size   Type      File system  Flags
 1      32.3kB  368GB   368GB  primary   ntfs         boot
 2      368GB   1000GB  632GB  extended               lba
 5      368GB   1000GB  632GB  logical   ntfs


Model: ATA WDC WD10EALS-002 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  8717MB  8717MB  primary   ext4
 2      8718MB  230GB   221GB   extended
 5      8718MB  221GB   212GB   logical   ext4
 6      221GB   230GB   9021MB  logical   linux-swap(v1)
 3      230GB   1000GB  770GB   primary   ntfs


Model: ATA ST31000528AS (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size   Type     File system  Flags
 1      230GB  1000GB  770GB  primary  ntfs


Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: /dev/sr1: unrecognised disk label                                  
====
Please note though, I have 3 1TB hard drives in this system; two of the drives are the same brand too & there are two partitions with the same name (on different drives), so this may be confusing.  "Why do the partitions have the same name" you ask?, Because I cloned one of th hard drives. I've installed Ubuntu on one of the drives that was cloned. The Ubuntu slice is the one that I want to resize. Yes, I'm going to rename one of the slices, because it IS confusing to have 2 slices with the same name! I just don't know how. 

Also, can I change the name of the slice by choosing to "Edit Partition"? If I do that, will I be able to JUST change the name of the partition or will I lose data?

THANK YOU!

---

### Post by kansasnoob on 2011-01-23
The only significant unused/free space I see is on /dev/sdc:

> Number Start End Size Type File system Flags
1 230GB 1000GB 770GB primary ntfs


It begins at 230GB so the 230GB preceding that are not used. I do not at all see what you're describing in your original post.

As far as copying partitions there are serious caveats, such as the UUID's needing to be changed.

---

### Post by bamim2 on 2011-01-23
What I'm referring to is the 212GB Linux filesystem, that sits inside the 221GB Extended partition. I want to slice up that extended partition because I was originally trying to make it 80GB. I was trying to just have it an 80GB filesystem & leave the other 150GB its own partition, but that didn't happen. 

I may just boot from the DVD & try it. The installation is only a few days old & if it messes it up, I won't be out much. Thanks for all the info so far.

---

### Post by oldfred on 2011-01-23
If you cloned drive the UUIDs may be the same and that causes all sorts of issues. You may not know which drive is being used.
To see UUIDs:

sudo blkid

You can shrink the Linux partition inside the extended and create a new partition in the free space.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

---

### Post by bamim2 on 2011-01-25
Thank you for all this info, but could you please point me to the one that shows me how to do that? I've followed all the links & that's a LOT of info to sort through. I appreciate the info, but it's just too much. I will be able to use all of this info going forward & it's ALWAYS good to have information, but I'd just like to know how to shrink my partition without losing my data. 

Additional info & question: I did clone one drive & when it was a Windows drive, Windows freaked out because of exactly what you said, it had the same ID & that caused problems so I took it off line (the Windows version of unmounting). That being said, I deleted the boot partition on one of the drives & I've deleted some of the VM on one of the partitions, so now they're not the same. Is there a "simple way" to change the name of the partition without jeopardizing the data in that partition? I thought I could just "edit" the label, but I'd rather ask somebody knowledgeable (you) rather than just try it & lose all my data.

THANK YOU for helping me out with this.

---

### Post by oldfred on 2011-01-25
If you look at the first link, it has simple instructions on resize partition. Literally you just drag the right side left. Be sure to swap off on the swap partition as the liveCD usually mounts it to speed up activities. 

Some like different presentations or more graphical views. That is why I post several alternatives, but each has enough info todo what you want.

---

### Post by bamim2 on 2011-01-25
Ahh, thanks. Sorry to be a bonehead, but I want make sure I don't hose this up. When you say, "the first one", do you mean the one entitled "GParted partitioning software - Full Tutorial" or the one entitled "Resizing an Ubuntu System Partition"? 

When you say, 'be sure to swap off...', what does that mean exactly? It sounds like I'd be turning off swap. If that's the case, how do I do that & how do I turn it back on? 

As I recall, GParted is not available in the Live CD/DVD version of Ubuntu, so can I "install it" somehow? Can I do that from the Ubuntu Software Center the same as in a normal Ubuntu session? 

Again, I consider myself to be new to Ubuntu. I have been doing it for a while, but I keep running across things I've never done before & as I'm sure you know there's a LOT of stuff to know. I'd rather ask dumb questions than make dumb mistakes. 

Yes, I know. I AM asking lots of dumb questions. :) I REALLY appreciate the help & AM learning a great deal all the time on this forum.

---

### Post by oldfred on 2011-01-25
Gparted is on the liveCD. It is just not installed as part of the standard install as you cannot use it on mounted partitions.

If you have a swap partition, then click on it (right click? - its been a while) and one of the options is swap off.  If you have little key symbols the partition is locked.

Either tutorial will work, they all cover the same info, just in different ways.

---

### Post by bamim2 on 2011-01-26
Thank you for clearing that up. I'll read the info & give it a shot. I'll see what happens & let you know the outcome. It sounds pretty simple, but I'll still read the info. Thanks again for hanging in there & helping me out.

---

### Post by bamim2 on 2011-01-26
I was able to successfully shrink my partition & create a new partition as I have been trying to do. Thank you for the help.

---

### Post by oldfred on 2011-01-26
I do not know if windows uses UUIDs. It also hides some windows serial number data somewhere in the MBR area.

Change UUID see also man pages:
uuidgen
tune2fs /dev/sdaX -U numbergeneratedbyuuidgen

---

