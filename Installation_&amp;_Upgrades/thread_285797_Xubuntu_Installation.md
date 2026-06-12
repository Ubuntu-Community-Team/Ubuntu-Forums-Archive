---
title: "Xubuntu Installation"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by ribena on 2006-10-27
I've just made my first attempt at installing xubuntu (6.10) on my desktop. I currently have multiple partitions with gentoo and windows on. When I try the installer it doesn't see any of my partitions! It recognises my hard drive but thinks it is empty (no partitions). The only options I have are to create a new partition (potentially wiping my current partition table and screwing my data). What could be causing this? Should I try just a normal Ubuntu install cd?

Thanks for any help

Rob

---

### Post by john_spiral on 2006-10-28
Hi Rob,

what file type are the other partitions? FAT, NTFS EXT2....

has anyone else had a similar scenario with xubuntu?

---

### Post by ribena on 2006-10-28
I have a couple of reiserfs partitions, one NTFS and one FAT32. Oh and a swap partition too...

Rob

---

### Post by markymark on 2006-10-28
hi Rob,

haven't thought out a solution for this yet. I get similar problem
[http://ubuntuforums.org/showthread.php?t=286931](http://ubuntuforums.org/showthread.php?t=286931)
but I can share what I know. 

I think the parted/gparted software
does not read the partition table written by whatever
wrote it last. In my case it was cfdisk.
& I know it will lose the rest of the disk if I dare
to go ay further with the partitioning.

I have tried edgy install cd, dapper install cd and alternative
install cd and a dvd of debian etch and the gparted live cd.
All are using the same parted/gparted software and so I'm not sure
this is resolvable. The only way forward seems to me to find
an alternative way of getting a minimum ubuntu/debian 
system onto the disk and then upgrading.](*,) 

best wishes,
Mark

---

### Post by ribena on 2006-10-28
Cheers for the reply Mark. Agree with your comments about gparted. I'm think install (x)ubuntu another way. I might try doing it from knoppix - link here:
[https://help.ubuntu.com/community/Installation/FromKnoppix](https://help.ubuntu.com/community/Installation/FromKnoppix)

Seeing as I'm replacing gentoo it should be a walk in the park in comparison to that install ;) 

Cheers

Rob

---

### Post by markymark on 2006-10-28
Hi Rob,

one further thing...I have found a way forward for me at least...

I'm now prepared not to blame debian/ubuntu/gparted, maybe cfdisk or diskdrake (used in the past on my disk) allowed me to do some quite dodgy things.

I'm currently running from zenwalk and having installed gparted
on this distro, when I start it from the command line
gparted complained about overlapping partitions,

I had a primary partition, then an extended partition
and then had intended everything else to be inside the
extended partition. But /dev/hda3, a small windows fat32,
was I think not part of the officially extended partition(???)
and I think this was what cause the problem to gparted.

I have used fdisk to edit the partition table and delete
/dev/ha10 and /dev/hda3
after further backing up of data.
(By the way, if I try to do ths with cfdisk it changes the
partition numbers, which is a sure sign that the disk
is going to be messed up. So don't write the data to the partition
table if this happens - oherwise its too late. I don't really
trust cfdisk now.)

Anyway, bottom line is that now /dev/hda3 has gone, gparted
wil read the partition table on zenwalk, so I guess will
now do so in the ubuntu and debian installers.

I've attached a summary of the info about the disk.

best wishes,
Mark

PS: a warning to any new users, reading this - all
these partition managers have the ability to lose 
your data on the disk and this has happened to me
in the past - so please back up data first!

---

### Post by ribena on 2006-10-29
Yeh I think my partition table it probably a bit fuxored to - too much hacking around with it in gentoo. I'll probably have to do a complete rebuild now... :|

Cheers

Rob

---

### Post by noranthon on 2006-11-14
There is nothing wrong with my existing partition table.  I have three working Linux installations on the disk, two empty partitions (one intended for Xubuntu), a Linux swap and an xfs partition containing data files, software and backups.

None of the partitions overlap.

I've read the preceding posts but do not see a way of installing Xubuntu. :confused:

---

### Post by noranthon on 2006-11-14
I should say no solution except the mind bender using Knoppix.  Is the kubuntu alternate installer any better?

And has anyone reported the bug?

---

### Post by noranthon on 2006-11-25
First, I filed [a bug report]("https://launchpad.net/distros/ubuntu/+bug/71894").

Secondly, I tried to overcome the problem by partitioning the whole of the hard drive.  That did not work, so I deleted all empty partitions.

Thereafter, the installer was able to identify the partitions and the unused space.  It allowed me to ascertain the number of sectors on the unused space but would not allow me to partition it.

My next move, if there is one, will be to add a partition using another distro or installer and install something on it that I'm happy to lose.  It seems that the Xubuntu installer is happy to use another distro's nest but will not build its own.

The so-called solution of using Knoppix is no remedy.  You may as well install Knoppix.

---

