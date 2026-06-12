---
title: "Has anyone converted ext3 to ext4 yet ?"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by BGFG on 2009-03-26
I've been looking at this documentation: [http://landley.net/kdocs/Documentation/filesystems/ext4.txt](http://landley.net/kdocs/Documentation/filesystems/ext4.txt)

and wondering if it's safe to attempt conversion on a drive with existing data. Backup is not an option, i have no extra storage...
I'd like to try it, but if it's really not advisable i won't. Anyone perform a successful conversion ?

---

### Post by madeinfamous on 2009-03-26
hello BGFG,

yess, since alpha5,

you need the name of your partition, then :

tune2fs -O extents,uninit_bg,dir_index /dev/sd**

were ** is your partition name,


and right after (important) :

fsck -pf /dev/sd**

this one could be long, depend on how many gig your partition is,



cheers, :)

---

### Post by lvlo on 2009-03-26
The same here... successfully convert my home partition to ext4 when migrate from 8.10 to 9.04 Alpha 6.

Used this tutorial: [http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html](http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html)

---

### Post by Delever on 2009-03-26
I suggest doing at least minimal backup.

---

### Post by Starks on 2009-03-26
Beware though, ext4 is still buggy. It can cause data loss, there is no meaningful to return to ext3 without using a spare hard drive, and Windows doesn't have a driver for it yet.

---

### Post by FuturePilot on 2009-03-26
I have converted my Jaunty machine to Ext4. I imaged all my partitions beforehand just in case. But so far everything seems to be ok. I'm still keeping an eye out for any possible problems.

---

### Post by BGFG on 2009-03-26
Great stuff, thanks all! :) My Home dir just has a bunch of movies and some documents. The docs i can back up, If the movies and anime get messed up, well whatever :)

did a fresh install with a 'daily' last friday, so / is already ext4 and quite fast, so i would like to see what kind of response i'll get from media files. 

On another note, not looking forward to the final release and the kernel included, as the included patches will cost some performance ...

---

### Post by Delever on 2009-03-26
I am running my system partition on Ext4, had no problems so far. My /home partition is still Ext3.

---

### Post by smartboyathome on 2009-03-26
The thing you don't want to do is forcefully shut down on an EXT4 partition (ie, shutting down by holding the power button until the power goes off). Doing so causes data loss for me.

---

### Post by Delever on 2009-03-26
> **smartboyathome said:**
> The thing you don't want to do is forcefully shut down on an EXT4 partition (ie, shutting down by holding the power button until the power goes off). Doing so causes data loss for me.

What is usually lost exactly? Random files, or recently saved files?

---

### Post by scottuss on 2009-03-26
The filesystem doesn't save things to the drive straight away so it may lose recent data (data older than a few minutes should get written and therefore would not be lost.) 

There was a bug where configuration files were getting lost but I think that's sorted now.

---

### Post by FuturePilot on 2009-03-26
> **smartboyathome said:**
> The thing you don't want to do is forcefully shut down on an EXT4 partition (ie, shutting down by holding the power button until the power goes off). Doing so causes data loss for me.

There were a few patches that were included to prevent this from happening.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/154]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/154")

> **Delever said:**
> What is usually lost exactly? Random files, or recently saved files?
Any file that was recently modified and is in the cache that hasn't been flushed out to the disk yet.

---

### Post by zika on 2009-03-26
> **smartboyathome said:**
> The thing you don't want to do is forcefully shut down on an EXT4 partition (ie, shutting down by holding the power button until the power goes off). Doing so causes data loss for me.
from what I read (I have not tried ext4 and I'm using data=ordered on my ext3) You can avoid such a situtation.
as far as I know ext4 has (sort-of)data=writeback as default (called "delayed allocation"). can it be made to have (sort-of)data=ordered (called "nodelalloc") mounting option? if You change that do You still have data loss? linus torvald:[http://thread.gmane.org/gmane.linux.kernel/811167/focus=811699](http://thread.gmane.org/gmane.linux.kernel/811167/focus=811699).
nice reading: [http://beta.linuxfoundation.org/news-media/blogs/browse/2009/03/delayed-allocation-and-zero-length-file-problem](http://beta.linuxfoundation.org/news-media/blogs/browse/2009/03/delayed-allocation-and-zero-length-file-problem)
from:[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4):> 
**Caveats**

 
 **[[edit]("http://en.wikipedia.org/w/index.php?title=Ext4&action=edit&section=15")] Delayed allocation may expose API bugs**

 The delayed allocation poses some additional risk of data loss in cases where the system crashes before all data has been written to the disk.
 The typical scenario is a program that replaces the content of a file, without forcing a write to the disk with [fsync]("http://en.wikipedia.org/wiki/Fsync"). If the system crashes shortly afterwards, it is really undefined what is supposed to happen. However, users have come to expect that the disk holds **either** the old version **or** the new version of the file, a behaviour that [ext3]("http://en.wikipedia.org/wiki/Ext3") would usually yield. Whereas the ext4 code in kernel 2.6.28 will often have truncated the file to zero length before the crash, but not yet written the new version, so that the contents of the file is lost.
 Though this is really an application bug, many people still find such system behavior unacceptable. In response, Theodore Ts'o has written some patches for ext4 that cause it to limit its delayed allocation in these common cases. For a small cost in performance, this will significantly increase the chance that a version of the file survives the crash.
 The new patches are expected to become part of the mainline kernel 2.6.30. Various distributions may choose to backport them to 2.6.28 or 2.6.29, for instance [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu") intends to make them part of the 2.6.28 kernel in Jaunty.[[9]]("http://en.wikipedia.org/wiki/Ext4#cite_note-8")

---

### Post by BGFG on 2009-03-26
Just ran it. 6.5 % non-contiguous files :)edited fstab at once, changed home to ext4. anything else i should do ?

restarted, conversion successful! now for the beta.....

P.S anyone happens across this thread, the conversion really IS that easy. Two commands, edit fstab, reboot. Just back up your sh** first :)

---

### Post by smartboyathome on 2009-03-26
> **zika said:**
> from what I read (I have not tried ext4 and I'm using data=ordered on my ext3) You can avoid such a situtation.
as far as I know ext4 has (sort-of)data=writeback as default (called "delayed allocation"). can it be made to have (sort-of)data=ordered (called "nodelalloc") mounting option? if You change that do You still have data loss? linus torvald:[http://thread.gmane.org/gmane.linux.kernel/811167/focus=811699](http://thread.gmane.org/gmane.linux.kernel/811167/focus=811699).
nice reading: [http://beta.linuxfoundation.org/news-media/blogs/browse/2009/03/delayed-allocation-and-zero-length-file-problem](http://beta.linuxfoundation.org/news-media/blogs/browse/2009/03/delayed-allocation-and-zero-length-file-problem)
from:[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4):

Thanks, I will try that line. I am on Arch, but have converted my disk to EXT4, so I thought I might as well pass on what I was having trouble with. Glad it was fixed in Ubuntu! :D

---

### Post by zika on 2009-03-26
> **smartboyathome said:**
> Thanks, I will try that line. I am on Arch, but have converted my disk to EXT4, so I thought I might as well pass on what I was having trouble with. Glad it was fixed in Ubuntu! :D
as far as I know it is not fixed ...

---

### Post by forcecore on 2009-03-26
i heard from digg.com comments that ext4 data loss is fixed now in ubuntu

---

### Post by mamamia88 on 2009-03-26
i did a fresh install with ext4 today and my last boot in intrepid was 49 seconds.   my last boot in jaunty with the exact same settings 26 seconds i think it's working

---

### Post by SuperSonic4 on 2009-03-26
> **Delever said:**
> I am running my system partition on Ext4, had no problems so far. My /home partition is still Ext3.

Same here, I've had this home for months and I might do a complete reinstall with ext4 except arch is a rolling release :popcorn:

---

### Post by markharding557 on 2009-03-26
one pitfall with converting to ext4 is this,if you want to revert back to the previous version of ubuntu you got problems because ext4 cannot be converted back to ext3 and intrepid does not support ext4.
worth bearing in mind.

---

### Post by syko21 on 2009-03-26
> **madeinfamous said:**
> hello BGFG,

yess, since alpha5,

you need the name of your partition, then :

tune2fs -O extents,uninit_bg,dir_index /dev/sd**

were ** is your partition name,


and right after (important) :

fsck -pf /dev/sd**

this one could be long, depend on how many gig your partition is,



cheers, :)

Can we get this stickied?

---

### Post by autocrosser on 2009-03-26
Well--I came on this thread late, but I was one of the first to convert to ext4 after talking to Theo about it...I have not had many of the problems that have whirled 'round this topic--all-in-all, ext4 works very well--I run a "mixed" system---Intrepid, Elive Gem & one storage drive are ext3 & Two Jaunty installs, Fedora11 & my second storage drive are ext4. I run 1.75TB's of storage & keep regular backups, so even if I crash I am back with a minimum of fuss.

A interesting bit of reading for all:  [http://ubuntuforums.org/showthread.php?t=1090488](http://ubuntuforums.org/showthread.php?t=1090488)

And the main thread: [http://ubuntuforums.org/showthread.php?t=965879](http://ubuntuforums.org/showthread.php?t=965879)

---

### Post by FuturePilot on 2009-03-27
> **markharding557 said:**
> one pitfall with converting to ext4 is this,if you want to revert back to the previous version of ubuntu you got problems because ext4 cannot be converted back to ext3 and intrepid does not support ext4.
worth bearing in mind.

You can't exactly downgrade to a previous version of Ubuntu so this seems like a moot point. The only way to go backwards is to reinstall.

---

### Post by markharding557 on 2009-03-27
what i meant was is if your home partition was ext4 then you would have to format it to ext3 when installing an older ubuntu so you would have to backup any data you wanted to save,whereas normally you don't need to

---

### Post by raiwo on 2009-03-27
when final comes out will ext4 be option there (in live cd) or do i need to use alternate cd?

---

### Post by wangsuda on 2009-03-27
On a related note, can a computer running Jaunty and formatted in ext4 read and write to an external hard drive formatted in ext3?

---

### Post by danwood76 on 2009-03-27
> **raiwo said:**
> when final comes out will ext4 be option there (in live cd) or do i need to use alternate cd?

I installed to ext4 from the live beta CD, so it will be in the final.

---

### Post by ykpaiha on 2009-03-27
Installed today as ext4 for/ and ext3 to keep my home.
Installed done with netinstall mini-iso
the first suggestion for installing was ext4 for the main partition. 
No problem so far.

---

### Post by Seren on 2009-03-27
Do you need to umount before using tune2fs ?

---

### Post by Milos_SD on 2009-03-27
I have one hard drive formated as ext4, and I want to convert /home and / on main hard drive to ext4. I read on some guides that it will just convert it for new data, and old data will still use indirect mapping to map all the blocks of data. And that some online defrag that I don't know how to use and where to find can convert it to extents format. Is that true, and how will that affect performance?

---

### Post by screaminj3sus on 2009-03-27
I have a fresh install of the beta with all ext4, very fast.

---

### Post by SuperSonic4 on 2009-03-27
> **madeinfamous said:**
> hello BGFG,

yess, since alpha5,

you need the name of your partition, then :

tune2fs -O extents,uninit_bg,dir_index /dev/sd**

were ** is your partition name,


and right after (important) :

fsck -pf /dev/sd**

this one could be long, depend on how many gig your partition is,



cheers, :)

Does this method cause data loss?

---

### Post by autocrosser on 2009-03-27
> **wangsuda said:**
> On a related note, can a computer running Jaunty and formatted in ext4 read and write to an external hard drive formatted in ext3?

In a word--Yes. I do it all the time---you just can't read a ext4 drive from a ext3 install--ext4 is backwards compatible. I am sure in time you will be able to read ext4 from ext3--but as ext4 is the next future filesystem--I really don't see the need....My guess is within the next 2 years ext4 will become the standard & ext3 will go the way of ext2 (and good riddance to it in my opinion.)

---

### Post by autocrosser on 2009-03-27
> **SuperSonic4 said:**
> Does this method cause data loss?

Not as far as I have seen---I have been using ext4 for close to 4 months now. I have only had 2 problems & both were very early on. With the next kernel (2.6.30), there will be several extra "safe-guards" built in, so there will less chance of data-loss. The best protection--regular backups & a close eye on your system.

---

### Post by BGFG on 2009-03-27
> **Seren said:**
> Do you need to umount before using tune2fs ?

nah, just use the commands posted earlier in the thread and ensure that you use 'sudo'

---

### Post by Bert Mariën on 2009-03-28
I surely would try the ext4, but I have a small (?) problem with that. I guess.

I have off and on 8 distro's on my machine, and I need to be able to access all drives from all drives, and not all distro's use ext4 yet.

But as I read here, ext4 is still buggy, so...
I'll wait till the most notorious distro's are compatible with ext4.

---

### Post by snkngshps on 2009-04-05
> **madeinfamous said:**
> hello BGFG,

yess, since alpha5,

you need the name of your partition, then :

tune2fs -O extents,uninit_bg,dir_index /dev/sd**

were ** is your partition name,


and right after (important) :

fsck -pf /dev/sd**

this one could be long, depend on how many gig your partition is,



cheers, :)

I'm getting this error when running the second command:

```
/dev/sda1: Clearing orphaned inode 23797784 (uid=1000, gid=1000, mode=0140755, size=0)
/dev/sda1: Inodes that were part of a corrupted orphan linked list found.  

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)

```

---

### Post by gjoellee on 2009-04-05
I've done it twice. All you need is a live medium and 1 command =)

---

### Post by BGFG on 2009-04-05
@snkngshps, These might help :)

[http://forums.devshed.com/linux-help-33/unexpected-inconsistency-run-fsck-manually-71202.html](http://forums.devshed.com/linux-help-33/unexpected-inconsistency-run-fsck-manually-71202.html)
[http://forums.devshed.com/linux-help-33/unexpected-inconsistency-run-fsck-manually-71202.html](http://forums.devshed.com/linux-help-33/unexpected-inconsistency-run-fsck-manually-71202.html)

---

### Post by mlissner on 2009-04-05
Has anybody tried this that uses the drive-level whole disk encryption thing? The one that's installed with the alternate iso? I'm guessing that would make no difference, but I'd hate to find out otherwise.

---

### Post by rplantz on 2009-04-05
> **Delever said:**
> I suggest doing at least minimal backup.

ValueOfBackup == CostOfRedoingEverythingSinceLastBackup;

---

