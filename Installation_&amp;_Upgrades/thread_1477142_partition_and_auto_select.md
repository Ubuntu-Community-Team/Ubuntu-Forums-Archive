---
title: "partition and auto select"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2010-05-08
I have following partition setup:
primary = boot,xp 12gig, ubuntu 20gig
extended = swap 4 gig,fat32 100gig , free 9gig

I load new Ubuntu disk.
I am given two options
install side by side and choose at startup - this cuts up my fat and leaves my free

or 
use largest free space
if i choose my free space (9 gigs), will I still be able to choose os at startup?
do i need to add more free space, is this all?

---

### Post by kansasnoob on 2010-05-08
> **pjmlmas said:**
> I have following partition setup:
primary = boot,xp 12gig, ubuntu 20gig
extended = swap 4 gig,fat32 100gig , free 9gig

I load new Ubuntu disk.
I am given two options
install side by side and choose at startup - this cuts up my fat and leaves my free

or 
use largest free space
if i choose my free space (9 gigs), will I still be able to choose os at startup?
do i need to add more free space, is this all?

If you have only one disc it's almost certainly /dev/sda so post the output of:

```
sudo parted /dev/sda print
```

If you have more than one drive post the output of:

```
sudo fdisk -l
```

and we'll go from there.

---

### Post by pjmlmas on 2010-05-08
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  18.0GB  18.0GB  primary   ntfs         boot 
 2      18.0GB  41.1GB  23.1GB  primary   ext3              
 3      41.1GB  120GB   79.0GB  extended                    
 5      41.1GB  45.3GB  4195MB  logical   linux-swap        
 6      45.3GB  109GB   64.1GB  logical   fat32             


not listed 9 gigs free at end

basically want to install  new Ubuntu version. 
so three choices at startup xp, ubuntu 8, ubuntu 9/10
Ubuntu 9/10 on single partition would be temporary until comfortable.

---

### Post by kansasnoob on 2010-05-09
Sorry to just disappear, I was tired :(

What I would do is boot the Live CD to the Live Desktop and use Gparted (it's in System > Administration) to create a new logical partition in that unpartitioned 9GB. Once created I think it will be /dev/sda7, remember that or write it down!

Then when you proceed with the installation choose Manual(advanced) as the option:

[http://members.iinet.net/%7Eherman546/p28/023_manual-partitioning.png](http://members.iinet.net/%7Eherman546/p28/023_manual-partitioning.png)

Next you'll see this screen:

[http://members.iinet.net/%7Eherman546/p28/024_change-ssd.png](http://members.iinet.net/%7Eherman546/p28/024_change-ssd.png)

Be sure to highlight **[COLOR="Red"]the new partition[/COLOR]** (you did write down the number, eh?) and click on Edit/Change, then you'll get this window:

[http://members.iinet.net/%7Eherman546/p28/025_ssd-done.png](http://members.iinet.net/%7Eherman546/p28/025_ssd-done.png)

Make the following selections:

New partition size: I'd leave unchanged (should represent the 9GB)
Use as: I'd select either ext3 or ext4
Format: YES be sure to "tick" that
Mount Point: /  Note: the "/" indicates root

When you're satisfied that's correct just click on OK which will take you back here:

[http://members.iinet.net/%7Eherman546/p28/028_partitions-done.png](http://members.iinet.net/%7Eherman546/p28/028_partitions-done.png)

Since that's the only partition you're creating just click on Forward and you'll next need to enter all of your personal info, then when you click on Forward you should see this:

[http://members.iinet.net/%7Eherman546/p28/032_install-now.png](http://members.iinet.net/%7Eherman546/p28/032_install-now.png)

Be sure to review all of that info (you'll see that the installer automatically chose sda5 as SWAP) and if it looks right just click on Install :)

Credit to Herman for the screenshots:

[http://members.iinet.net/~herman546/p28.html](http://members.iinet.net/~herman546/p28.html)

---

### Post by pjmlmas on 2010-05-10
/dev/sda1 = ntfs =winxp
/dev/sda2= ext3 = ubuntu current
/dev/sda3= extended
   /dev/sda5= logical part = linux-swap
   /dev/sda6= logical part = fat32
   /dev/sda7= ext3 = new ubuntu

was not sure that new logical part, /sda7, could hold os and still be choosen from boot menu, since it is in logical and not immediately following other oses.
/sda5 will be shared between old and new ubuntu versions?

nice screen shots :)   !

---

