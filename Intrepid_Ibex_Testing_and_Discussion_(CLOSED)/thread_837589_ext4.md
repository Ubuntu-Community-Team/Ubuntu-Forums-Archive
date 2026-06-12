---
title: "ext4"
date: 2008-06-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by articpenguin on 2008-06-22
i ask that the ubuntu devs add ext4 for intrepid. All the other distros include support for it even though it is not stable. For people who want to use have to add something to there ext3 superblock for it to mount.

---

### Post by olskar on 2008-06-22
[http://brainstorm.ubuntu.com/idea/4468/](http://brainstorm.ubuntu.com/idea/4468/) :)

---

### Post by inportb on 2008-06-22
I'm not sure if an experimental filesystem should be installed by default, but it would be nice to have such an option in the partitioning tool.

---

### Post by Eclipse. on 2008-06-22
My guess would be it will be made available but I doubt it will be default, that wont happen till intrepid+1/2.

---

### Post by Nullack on 2008-06-22
Default would be suicide but options would be nice

---

### Post by Gina on 2008-06-23
Yes, the option for users to try out on a spare test machine would be a good idea.

---

### Post by ShirishAg75 on 2008-06-23
+1 on that ;)

---

### Post by soccerboy on 2008-06-23
+1 for having an option.  Not the default fs because too many new users would pick that fs for their data partitions.

---

### Post by Col-1023 on 2008-06-25
There should be a prominent warning so new users know it's an experimental filesystem, and therefore may have problems.

---

### Post by syxbit on 2008-06-25
does ext4 even have life left in it?
it seems by the time ext4 is made default, btrfs will be available (the linux equivalent of ZFS)

i'm waiting for that :)

---

### Post by soccerboy on 2008-06-25
I am liking the results for the benchmarks that have been conducted so far.  If there is a benchmark of ext vs zfs, let me know.  I'd like to see how they compare.

---

### Post by ShirishAg75 on 2008-06-26
> **syxbit said:**
> does ext4 even have life left in it?
it seems by the time ext4 is made default, btrfs will be available (the linux equivalent of ZFS)

i'm waiting for that :)

I'm looking forward to btrfs as well . The GNU/Linux filesystem seems to be heading to a direction where we the users would be spoilt for choices. 

There is also a possibility though, that the developers may think of using say something like btrfs for server and ext4 for desktop (with an option to change it to whatever the user wants) ,  just an idea though . 

Also waiting for any news on any of the 3 file-systems as well.

---

### Post by syxbit on 2008-06-26
i agree that an unstable filesystem would be a bigger mistake than a beta firefox, that's for sure.
let Fedora get rid of the bugs (as they usually do with bleeding edge stuff) and then we can include it :)

---

### Post by soccerboy on 2008-06-26
> **syxbit said:**
> i Agree That An Unstable Filesystem Would Be A Bigger Mistake Than A Beta Firefox, That's For Sure.
Let Fedora Get Rid Of The Bugs (as They Usually Do With Bleeding Edge Stuff) And Then We Can Include It :)

+1

---

### Post by ShirishAg75 on 2008-06-27
just to add [http://rudd-o.com/archives/2008/06/24/zfs-on-linux-my-story-and-howto-you-can-have-it-too/](http://rudd-o.com/archives/2008/06/24/zfs-on-linux-my-story-and-howto-you-can-have-it-too/)

---

### Post by articpenguin on 2008-07-04
ext4 hacker ty tso made ext4 his default filesystem

[http://tytso.livejournal.com/57492.html](http://tytso.livejournal.com/57492.html)

---

### Post by Nullack on 2008-07-04
Im just not keen on using ZFS in user space with FUSE.

---

### Post by syxbit on 2008-07-05
your default filesystem should not be on FUSE.
that's why btrfs will be so great.
although we'll have to wait and see.
it would seem that btrfs is more for server, like zfs

---

### Post by kwagner on 2008-07-05
> **ShirishAg75 said:**
> just to add [http://rudd-o.com/archives/2008/06/24/zfs-on-linux-my-story-and-howto-you-can-have-it-too/](http://rudd-o.com/archives/2008/06/24/zfs-on-linux-my-story-and-howto-you-can-have-it-too/)
Is that init script really needed?. 
Because I start my whole zfs stuff with just **two lines** in rc.local :roll:

```


	# Load framework
	/usr/local/sbin/zfs-fuse && sleep 5
	/usr/local/sbin/zfs mount -a
	# End ZFS stuff #

```

---

### Post by bikeboy on 2008-07-06
> **articpenguin said:**
> ext4 hacker ty tso made ext4 his default filesystem

[http://tytso.livejournal.com/57492.html](http://tytso.livejournal.com/57492.html)

No doubt he has a good system of backups, unlike most people :)

---

### Post by Archmage on 2008-07-07
I still would like to have the option to use ext4 as a bootsystem. Of course with a big warning sign.

---

### Post by jmate24 on 2008-07-23
Hi i just have a quick question, Will intrepid use ext4? i know that it is backward and forward compatible with ext3, but would it be best just to do a clean install? i have 2 hard drives both with ext3, one is my root partition(250GB) and the other is my home(1TB) and i am wondering that when ext4 comes available to the public, if that all i have to do is wipe my root partition and keep my ext3 as my home partition using the manual partition setup if using 2 different types of ext? or 3 will that degrade performance when the root drive accesses my home partition to play my music and videos? and will the function calls of intrepid allow for improved performance while accessing usb storage?

Thanx for your input...
jmate24:)

---

### Post by olskar on 2008-07-23
Quick answer; no, it is not finished

Check this: 

[http://ubuntuforums.org/showthread.php?t=846655http://ubuntuforums.org/showthread.php?t=837589](http://ubuntuforums.org/showthread.php?t=846655http://ubuntuforums.org/showthread.php?t=837589)

---

### Post by Eclipse. on 2008-07-23
It will probally be available but ext3 will still be the default until at least 9.04.

---

### Post by TheAlmightyCthulhu on 2008-07-23
I just use XFS, it's better in many cases anyway.

---

### Post by aamukahvi on 2008-07-24
> **TheAlmightyCthulhu said:**
> I just use XFS, it's better in many cases anyway.

How is it better than ext4? The main advantage of XFS over ext3 was speed (right?), but ext4 is supposed to be much faster.

---

### Post by TheAlmightyCthulhu on 2008-07-24
> **aamukahvi said:**
> How is it better than ext4? The main advantage of XFS over ext3 was speed (right?), but ext4 is supposed to be much faster.

Most of ext4's improvements come from acting more like XFS, once you mount the volume with extents, which is ext4's biggest feature, it's now incompatible with ext2 or ext3.

ext4 and XFS are comparable in speed under ideal conditions, but XFS has the advantage:

XFS has a defrag utility, xfs_fsr, e4defrag is still experimental, not well tested, and not included in any distribution. (Yes Linux filesystems frag, with ext3 there's nothing you can do)

XFS still uses less disk space overhead.

XFS has been around for years and years, it's been debugged and you know what to expect.

XFS uses a fraction of the CPU resources that ext2/3/4, Reiser, etc.

So, XFS, for many reasons is the best choice of filesystem for Linux, really the only reason they ever did ext4 is cause companies would get crotchedy if they didn't have an easy upgrade path.

Oh yeah, and you'll need to run a utility that doesn't exist yet to convert all your ext3-stored files to use ext4 extents. :popcorn:

---

### Post by klange on 2008-07-24
> **TheAlmightyCthulhu said:**
> XFS has a defrag utility, xfs_fsr, e4defrag is still experimental, not well tested, and not included in any distribution. (Yes Linux filesystems frag, **with ext3 there's nothing you can do**)
Despite how wonderful XFS may be, that statement is blatantly false. There is a very specific process for defragging EXT3 partitions, there just isn't a defragger that is native to EXT3. The process, in short, is to do a quick convert to EXT2, run the ext2 defragger, and then convert back. While overly complicated, there is something you can do.

---

### Post by articpenguin on 2008-07-24
ext4 is getting close to being production ready. 

from 

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

As of this writing (mid-July, 2008, just after the release of 2.6.26), the ext4 code is functionally complete and functional enough that a few people are using it in production. However, it is still being tested and although the developers haven't lost any data yet, please be cautious and keep plenty of backups! 


I used it for a while in old fedora 9 install and i never suffered a problem from it. I just didnt like fedora and deleted it. I think e2fsprogs 1.41.0 has full ext4 support with extents and everything now.

---

### Post by TheAlmightyCthulhu on 2008-07-24
> **WindowsSucks said:**
> Despite how wonderful XFS may be, that statement is blatantly false. There is a very specific process for defragging EXT3 partitions, there just isn't a defragger that is native to EXT3. The process, in short, is to do a quick convert to EXT2, run the ext2 defragger, and then convert back. While overly complicated, there is something you can do.

Doing that to ext3 means you must take the partition offline, convert it to ext2, defrag it, and destroy all of it's journaling metadata, XFS defrags itself in a 2 minute pass roughly every 2-3 weeks (for me), without taking it offline or risking data.

---

### Post by TheAlmightyCthulhu on 2008-07-24
> **articpenguin said:**
> ext4 is getting close to being production ready. 

from 

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

As of this writing (mid-July, 2008, just after the release of 2.6.26), the ext4 code is functionally complete and functional enough that a few people are using it in production. However, it is still being tested and although the developers haven't lost any data yet, please be cautious and keep plenty of backups! 


I used it for a while in old fedora 9 install and i never suffered a problem from it. I just didnt like fedora and deleted it. I think e2fsprogs 1.41.0 has full ext4 support with extents and everything now.

Fedora 9 supports ext4dev, a lot of features of the filesystem aren't there, the tool to convert ext3 stored files to ext4 extents isn't there, and the disk tools are new and unproven (as is the filesystem), in other words, it's a mess to work with right now, and it well could eat all of your data.

I'm not saying it won't be ready ever, but certainly nothing I'd want any of my data on, at least for the next year or so.

Back away, let everyone else get burned....personally, I could use XFS indefinitely.

---

### Post by Gina on 2008-07-24
XFS sounds very interesting.  I've heard of it but not looked into it's merits etc. (must do some research).  Just run up GParted and checked out making a new partition in XFS format.  XFS is listed but greyed out so I can't create an XFS partition.  I guess I need some extra module loaded.  From what's been said it sounds like XFS could improve system performance - is this a significant improvement?

---

### Post by TheAlmightyCthulhu on 2008-07-24
> **Gina said:**
> XFS sounds very interesting.  I've heard of it but not looked into it's merits etc. (must do some research).  Just run up GParted and checked out making a new partition in XFS format.  XFS is listed but greyed out so I can't create an XFS partition.  I guess I need some extra module loaded.  From what's been said it sounds like XFS could improve system performance - is this a significant improvement?

There are a couple of downsides to XFS, nothing that would bother most people though.

1. It can't be mounted as /boot unless you want to use LILO instead of GRUB, this is because GRUB does some silly stupid things, and ext4 also has this problem right now, likely that fix for ext4 on /boot will also fix the XFS as /boot problem, since GRUB causes both of them.

You CAN mount XFS as the root filesystem "/", just not /boot.

Solution: 100-120 MB ext3 partition mounted on /boot

2. XFS cannot be shrank, only grown, using xfs_growfs.

Also, you'll want the xfsdump package if you want XFS, it contains many nice tools, like xfs_db which can debug the file system and give you fragmentation reports, xfs_growfs, and xfs_fsr (defrag).

xfs_fsr works as follows, say I have XFS mounted on /dev/sda3 and I want to defrag it for a maximum of 5 minutes, and a verbose readout of progress.

xfs_fsr /dev/sda3 -vv -t300

Then XFS will defrag for 10 passes over the filesystem, or 300 seconds, whichever occurs first, if it doesn't get it all, it will save it's place and start there next time :cool:

XFS also never needs you to run fsck, it is self-healing.

Call XFS the Black Leather Jacket of filesystems. :lolflag:

---

### Post by Gina on 2008-07-24
Thank you :)  I think I'll give that a whirl on my test PC - I'm not too worried if I mess it up and wipe both hard drives - I can just reinstall Ubuntu :lolflag:

---

### Post by TheAlmightyCthulhu on 2008-07-24
> **Gina said:**
> Thank you :)  I think I'll give that a whirl on my test PC - I'm not too worried if I mess it up and wipe both hard drives - I can just reinstall Ubuntu :lolflag:

Gina: XFS is very well debugged and tested, most of the remaining Linux problems were ironed out in 2.6.24 through 2.6.26, I would have no reservations at all about using it anymore, most valid criticism of XFS on Linux has been fixed.

Most of the problems were caused by IRIX being more advanced than Linux, but Linux has improved much since XFS was ported.

---

### Post by TheAlmightyCthulhu on 2008-07-24
> **Gina said:**
> is this a significant improvement?

Depends on what you're doing, in almost any event XFS is faster, with some operations (working with large files), the improvement can be up to 30% or better.

---

### Post by psyke83 on 2008-07-24
> **TheAlmightyCthulhu said:**
> Depends on what you're doing, in almost any event XFS is faster, with some operations (working with large files), the improvement can be up to 30% or better.

In my experience it's marginally faster *and* slower, depending on the system. It's universally slower on my older desktop PC (and by old, I'm talking Pentium 2 350Mhz with 196mb ram) and just a tad slower than EXT3 on my fairly recent laptop. It's just about evenly matched on my (also fairly recent) desktop. Some operations are faster on these newer machines, though some seem a lot slower (such as reading the dpkg database during package installation or untarring large archives). It definitely seems more CPU-bound than EXT3.

In my opinion, in technical terms it is a great filesystem and has its many uses, but you must recognize that it is not as flexible as EXT3. For example, it is most certainly *not* suitable for laptops due to the journaling method (similar to EXT3's writeback), where unwritten data blocks gets zeroed on recovery as a "security" feature.

During the testing cycle for Hardy (or possibly Gutsy, I'm a little rusty), my laptop was experiencing unrecoverable system freezes with the "intel" driver upon switching to VTs (unrelated to filesystems, and which is now fixed in the driver). I was also testing XFS at the time and asked a couple of developers in the #xfs IRC channel if they could recommend any filesystem tuning parameters to ensure better security against data loss during crashes (some kind of equivalent to ordered journaling). Their answer? Don't crash your machine so often or use a UPS...

This page gives a nice summary of XFS: [http://en.wikipedia.org/wiki/XFS](http://en.wikipedia.org/wiki/XFS)

---

### Post by TheAlmightyCthulhu on 2008-07-24
Homer Simpson: "Don't worry about Wikipedia son, we'll just change it when we get home."

---

### Post by psyke83 on 2008-07-24
> **TheAlmightyCthulhu said:**
> Homer Simpson: "Don't worry about Wikipedia son, we'll just change it when we get home."

Haha, should I expect recent edits warning of the impending wrath of The Almighty Cthulhu? :p

---

### Post by Nullack on 2008-07-24
btrfs is where its at

---

### Post by johnl on 2008-07-24
> **TheAlmightyCthulhu said:**
> Doing that to ext3 means you must take the partition offline, convert it to ext2, defrag it, and destroy all of it's journaling metadata, XFS defrags itself in a 2 minute pass roughly every 2-3 weeks (for me), without taking it offline or risking data.

Why, during normal filesystem usage, would you **need** to defrag ext3? 
> Modern Linux filesystem(s) keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system.
--[http://www.tldp.org/LDP/sag/html/filesystems.html](http://www.tldp.org/LDP/sag/html/filesystems.html)

---

### Post by psyke83 on 2008-07-24
> **johnl said:**
> Why, during normal filesystem usage, would you **need** to defrag ext3?

I have always thought of these kind of assertions as half-truths at best, or misleading at worst.

ext3's design helps to mitigate fragmentation, and it's much, much better than older filesystems including ext2, FAT and NTFS, for example, but it does fragment over time (like any other filesystem, and especially under low disk space conditions).

There are user-space defragmentation tools/scripts for ext3 [shake, and a few more whose names I don't recall], and I believe a touted feature of ext4 is defragmentation support - why would this be necessary if it's an incremental evolution of ext3? Well, perhaps due to the fact that ext3 is susceptible to fragmentation, of course.

---

### Post by TheAlmightyCthulhu on 2008-07-24
> **psyke83 said:**
> I have always thought of these kind of assertions as half-truths at best, or misleading at worst.

ext3's design helps to mitigate fragmentation, and it's much, much better than older filesystems including ext2, FAT and NTFS, for example, but it does fragment over time (like any other filesystem, and especially under low disk space conditions).

There are user-space defragmentation tools/scripts for ext3 [shake, and a few more whose names I don't recall], and I believe a touted feature of ext4 is defragmentation support - why would this be necessary if it's an incremental evolution of ext3? Well, perhaps due to the fact that ext3 is susceptible to fragmentation, of course.

Any file system fragments, and the longer it goes, the worse it gets.

After about 5-6 months, you really could stand a defrag, but ext3 can't do it.

---

### Post by bapoumba on 2008-07-25
Threads merged.

---

### Post by aamukahvi on 2008-07-25
Personally I use the following layout:

JFS:  / (including /boot)
* can use GRUB
* uses the least CPU
* fast file system creation (like XFS)
* may be slower than XFS/ext3 for large file tree operations (thousands of files spanning hudreds of directories) but I don't expect those on / .

ext3: /home
* best protection against data loss (full journal instead of metadata-only, as on JFS/XFS)
* extremely slow file system creation
* slow fsck

Some of the points are from [http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388) (from 2006).

---

### Post by jimv on 2008-07-29
Dear god, people flipped out about having FF3 beta in Hardy....I can't imagine the outcry over an unstable file system.

---

### Post by Gina on 2008-07-29
I found out why grub boot didn't find my new Hardy installation with XFS file system - I had the wrong HD boot order set in the BIOS :lolflag:  

It's all working now :)  Haven't yet noticed any difference - I'll run some tests later on with large files and heavily laden directories.

---

### Post by jnw222 on 2008-07-29
i would love it

at least hide the option so those who do not know about can't use and reserve it 

aka have to pre-format the desired partition

---

### Post by Nullack on 2008-07-29
> **jimv said:**
> Dear god, people flipped out about having FF3 beta in Hardy....I can't imagine the outcry over an unstable file system.

No one was suggesting it be default. In fact the developer has declared no more structure changes to ext4 so any issue would be code fixes.

---

### Post by almostlinux on 2008-07-30
We must make linux run well on NTFS to ensure windows VISTA compatibility. All these "ext" file systems would only make ubuntu more 'incompatible'.

Sincerely,
Aspiring Troll

---

### Post by Nullack on 2008-07-30
ntfs-3g is there for that

---

### Post by articpenguin on 2008-07-30
For the user to mount ext3 as ext4 they have to add test_fs to the superblock.

---

### Post by caryb on 2008-07-30
> We must make linux run well on NTFS to ensure windows VISTA compatibility. All these "ext" file systems would only make ubuntu more 'incompatible'.
 Gee I hope the intent of the poster was not to use NTFS in Linux:confused: Even Microsoft concede that there are problems with NTFS but they pulled there new FS for Vista at the last minute because of problems.


Cary

---

### Post by Nullack on 2008-07-30
Whats more, there are windows apps for reading ext3 filesystems. ext3 is a better filesystem than ntfs, and we have support for reading/writing ntfs on Linux.

---

### Post by RAOF on 2008-08-01
> **caryb said:**
> Gee I hope the intent of the poster was not to use NTFS in Linux:confused: Even Microsoft concede that there are problems with NTFS but they pulled there new FS for Vista at the last minute because of problems.


Linky?  The filesystem I remember being pulled from Vista was some super-awesome [GNOME Storage](http://www.gnome.org/~seth/storage/)-like database-backed super FS.  Which got pulled fairly early, and Vista ended up with a new NTFS version.  Which isn't particularly bad; it just isn't the flying car they'd initially promised.

---

### Post by Archmage on 2008-08-01
Since we are only a month away from Feature Freeze: Will there ext4 in Intrepid Ibex?

---

### Post by Nullack on 2008-08-01
RAOF Vista got atomic transactional features added to its new version of NTFS, WinFS was canned in the longhorn dev which is closer to a relational DB than a filesystem.

---

### Post by The Keeper on 2008-08-04
The problem with JFS and XFS is lack of popularity and thus someday lack of active maintainers may become a real issue. File systems are delicate and complex, thus no average joe linux developer may be able to fix bugs that may crop up. It has been my fear that JFS and XFS may become deprecated in kernel.

And GRUB2 is taking its sweet time to reach a stable release. Seems unlikely the /boot volume issues with XFS and few other file systems are going to be fixed in 0.9 branch.

With a few changes to JFS/XFS journaling they would have been superb alternatives to ext3/4 even on desktops without backup power and notebooks. It is a real shame popularity of such advanced file systems is severely lacking.

:(

---

### Post by articpenguin on 2008-08-04
> **The Keeper said:**
> The problem with JFS and XFS is lack of popularity and thus someday lack of active maintainers may become a real issue. File systems are delicate and complex, thus no average joe linux developer may be able to fix bugs that may crop up. It has been my fear that JFS and XFS may become deprecated in kernel.

And GRUB2 is taking its sweet time to reach a stable release. Seems unlikely the /boot volume issues with XFS and few other file systems are going to be fixed in 0.9 branch.

With a few changes to JFS/XFS journaling they would have been superb alternatives to ext3/4 even on desktops without backup power and notebooks. It is a real shame popularity of such advanced file systems is severely lacking.

:(


Reiserfs is unmaintained and i think it will become depricated way before jfs or xfs do.

---

### Post by Archmage on 2008-10-15
Since the BETA is now out. What about ext4? Can I somehow use it without making my own kernel?

I would love to use it on some non important partition.

I did notice that you can't choose it when installing.

---

