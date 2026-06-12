---
title: "Problem mounting root during edgy installation"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by Dave Burbank on 2007-01-05
I am trying to install edgy off of a live cd, but I when I try to mount root '/' to a partition I created with a prior install of dapper, the installation program wont let me.

I am dual-booting with xp so I am unable to do a complete reformat, as I need to keep the windows partitions untouched.  I have created a primary partition for root (ext3), a logical partition for /home (ext3), and one for swap.

Here are two screenshots of the partition manager during installation:
sda3, sda4 and sda7 are the partitions I am trying to mount to with root, /swap, and /home respectively.

[ATTACH]22323[/ATTACH]

[ATTACH]22324[/ATTACH]
I appear to have "given" root a place to mount but notice the error.

I have use this exact setup for dapper, what could I be doing wrong?
Thanks

---

### Post by Dave Burbank on 2007-01-05
I found the answer here :
[https://launchpad.net/ubuntu/+source/ubiquity/+bug/67130](https://launchpad.net/ubuntu/+source/ubiquity/+bug/67130)

It is a known bug that edgy cannot mount root to a preexisting partition.

---

