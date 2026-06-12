---
title: "Partition Sizes"
date: 2014-02-19
forum: Installation &amp; Upgrades
---

### Post by borgward on 2014-02-19
.I want to make /, /home, /tmp and swap partitions. 

I really do need a large /tmp partition. It will be in the 20GB range.

How big do I make /?

Swap will be 1.5 x RAM.

Use as Ext2 , Ext3 Journaling file system? I am thinking 3 for all. Of course, swap will be swap.

I am pretty rusty on partitioning. Used to do from command line. I am doing this on an extra HDD, so I don't mess up the 750 GB HDD I have 14 installed on, and get a chore done that /tmp is too small to do.

Any reading resources for partitionaing.

---

### Post by Topsiho on 2014-02-20
I usually create 3 partitions: /, /home and swap. File system for / and /home is ext4, which is quite standard now.
/ is 5 to 20 GiB, depending on size of hard disk. 5 is minimum, 20 is far more than necessary, so quite enough.
swap is 1 to 2 times Ram, as a rule of thumb. 1 time when there is a lot of Ram, say 2GiB or more, 2 times when there is less Ram.
I play safe, and always use 2 times or even more Ram, in a large hard disk I feel I have ample space for this.
The rest is for /home, which contains all user files, for all users, and the config files. The more space in /home, the more and the larger files you can put into it.

Why do you want a separate partition for /tmp? If you need much space for this you can create a larger partition for / than I recommended above. I checked my /tmp as it is now and it is real tiny (almost empty).

A separate /home makes it easy to upgrade to a newer version, or install an other version of Linux, but should always be backed up first.

Topsiho

---

### Post by TheFu on 2014-02-20
**man parted**
But that won't help with the details around updating the fstab to connect all the new partitions to the OS and it won't help migrate the data from the existing locations. It is probably easier to do a fresh install and go into an advanced partitioning setup.

The default file system should be ext4 now unless you have specific requirements against doing that.

Swap over 4G is a waste. The old rules of thumb for 1.5-2x RAM don't apply anymore.

While you can setup all these extra partitions, if you like, but it seems like extra work for very little gain from here. Just make / as large as you need for it AND for /tmp.  /home and swap partitions can be whatever you like. Those are relatively easy to connect on a running system - though I'd just create a /h2 and put userids into it instead. Much easier.

There is NOTHING special about the "/home" location or name.  As long as the password entries point to where ever the home is, it can be named anything ... or even be located on a different physical machine and mounted via NFS. I've worked at mainly places where HOME directories came form different servers.  /h1, /u1, /u2, /u100,  /export/home ... whatever we needed.

---

### Post by fantab on 2014-02-20
This is a good tutorial about Gparted: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Ext4 filesystem is default. Use it unless you have some special need for Ext3.
If you have good RAM Gigs then you a SWAP partition of about 1-2Gb is plenty. However, if you 'Hibernate' your PC then you need SWAP size equal to or more than your RAM in GiB, not GB.
Is there any real reason why you want a separate '/tmp' partition? Generally you don't need it, everything under '/' partitions should suffice.

---

### Post by sandyd on 2014-02-20
posts in duplicate thread merged

---

