---
title: "prepare disk space problem"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by sdowney717 on 2007-04-12
all I see is

How do you want to partition the disk?

guided - use entire disk
or

guided use the largest contiguous free space

or 

manual


BUT, where is the resizer that I have always seen before?
the slider bar you move to change the ntfs windows partition?

I am not going to eliminate windows media center 

very confused

---

### Post by sdowney717 on 2007-04-12
ok, I discovered that I had 3 partitions.
one for windows
one for recovery
one unknown ??

So, I deleted these extra partitions leaving only the active xp partition.
THEN, the resizer appeared upon booting from live cd and going into install.

So, perhaps it could not resize due to the other partitions.

---

### Post by grimpage on 2007-04-13
Yeah I'm having a similar problem. 

Turns out you can only create a max of four partitions, using Gparted (the most up-to date program I know of) creating a serious problem for your (and my) backup slices. 

Have you happened upon a bypass for this? 

I've been trying to duel Xubuntu, which requires three slices to be happy, with XP creating one less space than there needs to be on the only physical drive I own! I'm really not ready to get rid or XP or my backup.  

Is Ubuntu different where it only requires two, or even a single partition to appease its demands?

Can one of Xubuntu's memory need's be shared with XP without reformatting?

I'm not really in the mood to start screwing around with my data, it's just too damn scary!

---

### Post by louieb on 2007-04-13
its good to be scared when resizing your windows partition. scared enough to have your data backed up before you begin. 
Any flavor or Linux can get by with 1 partition for the / (aka root file system) but most installers if you let them do there thing automatically will create a swap partition also (virtual memory in windows terms).  
All the flavors of Ubuntu including x and k install  very much alike.   
The slider is in two places manual partitioning and guided use largest contiguous free space. Be sure to defrag your window partition before you begin.   

The installer tries to setup your partitions the simplest way it can. But you are not limited to 4 partitions. You are limited to 4 primary partitions. more that that? requires the use of extended and logical partitions. (no there not just Linux things, windows does it that way also). 
For example here is my partition table on the P4 right now it boots XP, Ubuntu Dapper and Feisty, and PCLinuxOS.  The last partition is for sharing data between Linux and XP. 
```

lou@blackboxu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10207    81987696    7  HPFS/NTFS
/dev/sda2           10236       11528    10386022+  83  Linux
/dev/sda3           24257       24321      522112+  82  Linux swap / Solaris
/dev/sda4           11529       24256   102237660    5  Extended
/dev/sda5           11529       12821    10385991   83  Linux
/dev/sda6           12891       16663    30306591   83  Linux
/dev/sda7           16664       17999    10731388+  83  Linux
/dev/sda8           18000       23167    41511928+  83  Linux
/dev/sda9           23168       24256     8747361    b  W95 FAT32

Partition table entries are not in disk order


```
Just back up your data. be prepared to reinstall XP and the install should go smoothly. Just be sure to read everything before you press that install button.

---

### Post by grimpage on 2007-04-14
Yeah turns out that extending my partitions was a snap. Makes me feel kinda silly for asking so much about it. Ah well. My question now is:

Does it matter where the partitions for a single use (ie xubuntu) are on the physical drive?

I'll try to draw you a picture:

[Backup] [Extended /,/swap,/boot] [XP] [/home]

The XP partition is by far the largest of the four but it is tucked in between the two partitions I had planned for xubuntu, and I was just wondering if that will cause any performance issues.

Let me know what you think, it would be nice to only have to do this once. It took about 5-7 hours (I stopped watching after the third hour) of re-partitioning to get this set-up, and it wasn't even the first time I had tried! I didn't think about performance or logistical conflicts until much after the changes where being made.
Another quick question:

Would there be any way to hypothetically leave out the inclusion of say a /bin partition, but then be able to go back after any period of time and add any particular partition? 

Or would a fresh install, and repartition be required?

Thanks for any input.

---

### Post by bulldog on 2007-04-14
Let  windows on the **first primary partition** otherwise you get big boot problems with it.

It's depending on how much partitions you would have.
If you want to make an extended partition,you can only make three primary's.
There's no big difference between primary and logical partition,you wouldn't notice which one you use,**but** windows will **not** boot from a logical partition!!

So lets assume you want 6 partitions,think first what you want to do with them,and the size of them before you begin.
It makes no difference for ubuntu where it's located,only windows is the hard one.
No download the gparted live cd and burn it to a cd-r,boot this cd and you have a graphical partitioner,which is easy to work with.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Create your partitions as you like,I should make three primary's,one extended [this should be as big as the free space you have left] and create as much logical partitions as you want to have.
If all the space is used,take a good look if this is what you want to have,and hit the apply button.
Now your partitions are created,this could take some time.

Some advice about the ubuntu partitions.
Make a 10GB / (root) primary or logical,it doesn't matter and format it ext3
Make a 1GB swap partition,again,it doesn't matter if it's logical or primary and format it a s swap.
Create a /home partitions as big as you like for your personal data and preferences,this becomes very handy when you do a reinstall,format it as ext3.

Now you only have to mount this three partitions when you install ubuntu,the partitioning is done already.

But remember to make the first primary your windows partition,where you put your backup,ubuntu or what ever isn't that important,and is more a personal preference were you want to put your data.

---

### Post by Beezleblub on 2007-04-20
I have a 300GB hdd, wanted to make fresh Feisty installation on it.

I create partitions as follows :

30 GB size, Ext3  /
3GB Size  SWAP
the rest I want to be XFS 

when I try to create the 3th partition, I get an error : "can't have the end before the beginning"

weird, because the same thing did work in 6.10  ? ?

now tried to make only 1 xfs partition, full size, same error.
but I try to make a xfs partition smaller then 220 GB, it's ok ! 
so now I made
XFS 220 GB
Swap 5 GB
ext3 100 GB

but I don't want a 100 + GB system partition, I need the size in my XFS partition...
Any ideas why this is ?

Thanks !

---

