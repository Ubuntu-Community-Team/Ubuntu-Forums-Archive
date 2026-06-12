---
title: "[SOLVED] Suggested file system?"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by FrostDust on 2008-04-29
I am planning on installing a fresh copy of (k)ubuntu on my computer, and saw on the partition editor several different options for what I should format the partition with. I haven't been dissatisfied with ext3, but I was wondering if any of the other choices would offer any improvements.

I'm gonna be using this machine as a normal desktop, not for anything fancy like a mail server, etc. I don't need it to be accessible from other OS's, and I won't be doing any unusual hard drive configurations like RAID 1 or something. Any advice you may have would be appreciated. Thanks.

---

### Post by acelin on 2008-04-29
Ext 3 really is the best. It works the best by far, and i would suggest not using ext 3 and say ntfs or fat 32 on the same hard drive.

---

### Post by martrn on 2008-04-30
> **FrostDust said:**
> I am planning on installing a fresh copy of (k)ubuntu on my computer, and saw on the partition editor several different options for what I should format the partition with. I haven't been dissatisfied with ext3, but I was wondering if any of the other choices would offer any improvements.

I'm gonna be using this machine as a normal desktop, not for anything fancy like a mail server, etc. I don't need it to be accessible from other OS's, and I won't be doing any unusual hard drive configurations like RAID 1 or something. Any advice you may have would be appreciated. Thanks.

ext3 and reiser are comparable, they are both journal filing systems .  There is no benefit to using either over the other.  ext2 will slow your system down, if you are ever thinking of moving to a different distribution then using reiser or ext3 would have been an issue, but not any more.

Some disk partition tools push unwanted figures into the partition table by miscalculation a few blocks so if you are thinking of having ext 3 /reiser  on the same drive as ntfs or fat 32 make sure you backup your system before you loose all of it.

---

### Post by FrostDust on 2008-04-30
> **martrn said:**
> ext3 and reiser are comparable, they are both journal filing systems .  There is no benefit to using either over the other.  ext2 will slow your system down, if you are ever thinking of moving to a different distribution then using reiser or ext3 would have been an issue, but not any more.

Some disk partition tools push unwanted figures into the partition table by miscalculation a few blocks so if you are thinking of having ext 3 /reiser  on the same drive as ntfs or fat 32 make sure you backup your system before you loose all of it.

I am planning on dual booting, with Win XP on the same drive, so I'll make sure to do that. I guess the choice I'm looking at now is ext3 vs. XFS vs. JFS. Wikipedia seems to suggest that ext3 is slower compared to the other two. Basically, I guess my question is whether I would see any benefit on my desktop from using XFS/JFS compared to ext3.

---

### Post by sonofusion82 on 2008-04-30
ext3 while stable isn't the best performing and has its limitations
I personally prefer XFS. I have used it for my data partitions and it has been performing well.

---

### Post by finite9 on 2008-04-30
im not an expert by far, but here is my 2 cents:

ext3 is stable, works with all file system checking tools, is fully integrated with other tools and has a safe upgrade path to future versions of ext, namely ext4.  I use ext3 on all partitions.

XFS is popular because in *some* conditions it can really outperform ext3 and some other filesystems, but not all tools are integrated.  Dont ask me which because I dont remember, but think things like fsck, partitioning etc etc.  these are just examples.  im not saying that fsck does not work with XFS.  If you want to know what doesnt work, read the homepage of XFS.  They are only minor incompatibilities, but I dont want to get into a situation where I need to change the filesystem and cant due to limited support for external tools.  Bear in mind, that XFS does not always outperform ext3, only in certain circumstances.

JFS is IBMs journaling filesystem.  Only pro blem here is no upgrade path.  If they later release a newer version of JFS, then it's probably a reformat.  with ext3 to ext4 you can "upgrade" without reformat.  Apart from that JFS is comparable to ext3 feature wise.

Reiser is a dead dog.  Why people recommend this is beyond me.  Yes it performs great *in some conditions* but there is no upgrade path, the author has been convicted of murder, and its future development / bug fixes are in serious doubt.  Even before the Resire trial, there were some quite serious stability issues with this fs that offset the fact that it performed great in *some conditions*.

There are advantages and disadvantages of most filesystems, and there is no one silver bullet (well maybe but more on that in next paragraph).  Ext3 has the best outlook at the moment.

Lastlt, Suns ZFS is what appears to be a superb filesystem that is generations ahead of the others, but it's not currently available in most distros and I do not know if it is open source.  On paper it sounds fantastic, but if it's not open source it may be better waiting to see if ext implements similar features to compete with ZFS.

There are a few performance comparisons on the web between the different filesystems if you are that interested, but the general result is that they outperform each other in certain conditions and perform worse in others.  In my eyes, that means that it boils down to compatibility and management rather than performance.

---

### Post by recover89 on 2008-04-30
I just wanted to let you know that you can access your ext filesystems in windows using an [Ext2 IFS driver]("http://www.fs-driver.org/").
I'm using it and it works great! :D

---

### Post by mannheim on 2008-04-30
I'd like to emphasize one of the points in finite9's post: Often you see the statement that XFS is "faster" than ext3. But it depends what you are doing and how the filesystem is configured. I tried my own experiment once, formatting two empty partitions with ext3 and XFS, and tested untarring a large tar archive (containing many small files) on both. In my setup, XFS was much, much slower at this one specific task (a factor of three). So I decided I would stick with the default ext3.

---

### Post by FrostDust on 2008-04-30
Thanks for the advice, everyone. Due to the aforementioned compatibility reasons, I'm gonna stick with ext3 for now.

---

### Post by Em-Buntu on 2008-05-06
ZFS is open source.

I'm about to install just to get the self healing and super high reliability aspects of ZFS. 
As you said, it's features are miles ahead of other file systems supporting 128 bit addressing. I'll never have a need for a billion billion bytes of data, but it's nice to know you have such an advanced file system protecting your data.

I don't really care for Solaris. I think at this point in time Ubuntu has much more flexibility. All I want is ZFS and once I play around with it, I'll try to build ZFS into Ubuntu.

Update: 
ASUS K8N-DL Server/Workstation board. The Device Manager found everything on my workstation except 3 devices;

1. MIDI port
2. Silicon Image SATA Controller
3. Game port

Of the 3 I would only miss the Silicon Image controller when I get around to building a BIG RAID.
It's not a show stopper since it does see my NVIDIA RAID as well as my add-in LSI Logic SAS controller.

I suspect it runs so well on my workstation because it's an Quad Opteron (dual 800 series dual cores) system, and Sun is a BIG Opteron user. I noticed though, when I downloaded the LIVE CD, it didn't have an x86 32 or 64 option, Just languages.

For some reason System Monitor says this is a release candidate 3, not a formal release. This system manager is the same as the version used in Feisty and Gutsy. Not as slick as the new one in Hardy.

After playing with this, I think I'll put it on another system by itself to use as a NAS/file server with backup for my other systems. The ZFS system should add great reliability for backing everything up to it. I really find the idea of having a @self-healing@ file system appealing to handle file corruption and degradation.  This means my files should be safe through everything from a crash to power outages, excluding every but a total disk failure.
It seems to read or recognize ext3 format. I'm not too sure that Ubuntu will recognize ZFS though, and I'm not going to take the chance installing it on the same system or disk.
I may install it on another disk tomorrow just to play with it a little more.

Overall, I'm impressed with the speed, appearance, and capability of OpenSolaris. I expect, it will just continue to get better and better with each update.

At this point, I'd give the developers an A. I may up/down this grade later on as I get more hands on with ZFS.

---

### Post by articpenguin on 2008-05-07
zfs wont get into the kernel unless sun changes zfss license as the linux kernels license is incompatible with the license zfs is under.

BTRFS will own zfs when it is ready =)

---

### Post by Em-Buntu on 2008-05-07
Thanks. 
It's good to know Ubuntu is looking to add something comparable to ZFS sometime in the future. Sun says move ZFS under the GPL3 license.
The Linux kernel man says he doesn't like GPL3, so we'll have to wait and see.

Sounds like BTRFS is, Better File System? Where are the planned features listed?

The immediate availability of Zetabyte File System (ZFS) to OpenSolaris is a HUGE differentiator...and it's available today. So I'll have to update my TB file server from the tried and true, Windows2000 (running for 5 years now), to OpenSolaris. 

My workstation remains with Ubuntu and ext 3, and Windows-XP 64 with NTFS.

---

### Post by mrcorey on 2008-05-07
Good luck with your choice of EXT3.  I've had the best luck with ReiserFS.  I've been using the 3.x branch since it began and have found no instability problems at all and neither have most others.  I don't know why anyone thinks that its a dead system or that its not stable.  Namesys is still in business and its a free system, so it can be developed or forked.  The 4.x branch can be unstable, so I'd not go down that road (that was Hans' baby).

I lived in a rural area where the power went out unpredictably and I'd have a lot of unplanned shutdowns.  EXT2 and EXT3 always let me down, becoming unbootable after a few crashes like that.

Most people (sometimes without a lot of experience with different filesystems) have the opposite view as I do, so that's what makes the world turn.

Once again, good luck with your choice of EXT3.  I hope that it keeps you going strong for a long time.

---

### Post by solitaire on 2008-05-07
> **mrcorey said:**
> .I've had the best luck with ReiserFS.... I don't know why anyone thinks that its a dead system or that its not stable..

Think it's due to Reiser doing 25 to life in the state penn....:confused::confused:

---

