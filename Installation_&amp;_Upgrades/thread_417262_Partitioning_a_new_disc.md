---
title: "Partitioning a new disc"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by garbergs on 2007-04-21
Hi everyone!

I have a 500GB SATA disc that I want to use for a webserver. Here are my partitions:

sda1 primary ext3 30.0 GB, /
sda2 extended, logical 435.76 GB
sda5 swap 10.0 GB
sda6 ext3 20.0 GB, /var /temp
sda7 ext3 5.0 GB, webfiles
sda8 ext3 400.76 GB, database data

The sizes of each partition is what Gparted reports. When I start fdisk and choose "verify partition table" it says 5413 unallocated sectors. From what I understand that is about 2 MB so it's no big deal. Shall I just ignore this?

Gparted also reports that the new partitions are somewhat used. For example the large 400GB-partition is 6.49 GB used. Does this have to do with ext3? Should I ignore this as well?

Btw, after reading several threads, I have chosen ext3 for stability and data safety. And the sizes of some of the partitions are probably a bit large, but I figured it's easier to insert a new disc if needed, than to go back and resize the partitions. Any comments on this is also welcome!

---

### Post by mhansen on 2007-04-21
You're fine.  That unallocated space was (I believe) something that was deleted that is still there, but yet to be overwritten.

And formatting ext2/ext3 reserves (again, I believe) 5% of the disk space that is only accessible by root, for security reasons (aka, some butthead decides to fill up your disk space), and u need to get on and fix it.


You're good.  Except for that 10gb of swap.  Wasted space IMO.


Regards,
Mike

---

### Post by garbergs on 2007-04-22
OK, thanks!

I have another disc where I will store pictures and videos. 
Do I need any primary partition on this disc, 
or can I just have an extended with a few logical partitions? 
Will I be allright choosing disc label as "msdos"?

---

### Post by Lamar on 2007-04-22
> **garbergs said:**
> Hi everyone!

I have a 500GB SATA disc that I want to use for a webserver. Here are my partitions:

sda1 primary ext3 30.0 GB, /
sda2 extended, logical 435.76 GB
sda5 swap 10.0 GB
sda6 ext3 20.0 GB, /var /temp
sda7 ext3 5.0 GB, webfiles
sda8 ext3 400.76 GB, database data

The sizes of each partition is what Gparted reports. When I start fdisk and choose "verify partition table" it says 5413 unallocated sectors. From what I understand that is about 2 MB so it's no big deal. Shall I just ignore this?

Gparted also reports that the new partitions are somewhat used. For example the large 400GB-partition is 6.49 GB used. Does this have to do with ext3? Should I ignore this as well?

Btw, after reading several threads, I have chosen ext3 for stability and data safety. And the sizes of some of the partitions are probably a bit large, but I figured it's easier to insert a new disc if needed, than to go back and resize the partitions. Any comments on this is also welcome!

I'm not sure what kind of server you're setting up but I'd like to make some suggestions about your partitioning scheme if you don't mind. First, I'm not sure how much RAM you have on this machine but that swap partition is huge. Conventional wisdom (which is now outdated) is that your swap partition should pretty much match the amount of RAM you have; so if you have 1/2 gig of RAM you'd want 1/2 gig of swap. The fact is that with the amount of RAM that's becoming the norm nowadays, you very rarely, if ever, use swap. For example, my machine has 2 gigs of RAM and it never pages to swap at all.

I personally think that the new conventional wisdom should be that if you have at least one gig of RAM, then the buck stops there on matching the amount. Even with one gig of RAM you'll almost never use swap. Another piece of conventional wisdom that still holds true is to put your swap partition at or near the beginning of the drive since that's the fastest read/write area (remember, swap is being used as memory).

Here's a scheme that's extremely simplistic. Unless you have some really compelling reasons, I see no need to have separate partitions for /var/temp or your database, and the placement of the partitions seems odd to me as well; no offense meant.

```
sda1  primary  linux-swap  1024 MB  swap
sda2  extended
sda5  logical  ext3  128 MB  /boot
sda6  logical  ext3  (the rest)  /
```

[edit] I forgot to mention: when using ext3 the sizes you set get warped a bit because the filesystem takes up some space.

---

### Post by garbergs on 2007-04-22
Thanks for the advice, Lamar!

My webserver has 2GB of RAM, but I'm planning to upgrade to 4GB in the future.

I found some guides about partitioning, starting here:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

That thread references this guide, also very good:
[http://www.overclock.net/linux-unix-mac/11208-linux-partitioning-guide.html](http://www.overclock.net/linux-unix-mac/11208-linux-partitioning-guide.html)

There, you can read this:

> The temporary and variable /tmp and /var paths in linux respectively are separate for security reasons. These locations are publicly writeable and having them in with the rest of the operating system can cause a denial of service attack. Additionally any user can write to their home directory so you also want that separate from the rest of the root filesystem as possible. If the root filesystem's partiton should ever become completely full the system will crash and most likely be lost. Keeping these areas separate will save you alot of headache in the long run and is much safer than simply setting software disk quotas.

And on
[http://www.pathname.com/fhs/pub/fhs-2.3.html#THEFILESYSTEM](http://www.pathname.com/fhs/pub/fhs-2.3.html#THEFILESYSTEM)
you can read this:

> Disk errors that corrupt data on the root filesystem are a greater problem than errors on any other partition. A small root filesystem is less prone to corruption as the result of a system crash.

So now my latest plan is this:

sda1 PRIMARY /boot ext3 200 MB
sda2 PRIMARY swap 2 GB
sda3 PRIMARY / ext3 10GB
sda4 EXTENDED
sda5 LOGICAL /tmp ext3 5 GB
sda6 LOGICAL /var ext3 10 GB
sda7 LOGICAL /home ext3 (the rest)

And I'm guessing that the corresponding fstab would look something like this:

/dev/sda1 /boot ext3
/dev/sda2 none swap
/dev/sda3 / ext3
/dev/sda5 /tmp ext3
...and so on.

---

