---
title: "File System - EXT3 vs ReiserFS vs JFS"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by undoIT on 2008-10-26
Generally when I install Linux, I go with EXT3. I've been running Ubuntu 7.10 - 8.04 from the day they came out and haven't had any problems with data corruption while using EXT3. Since 8.10 is almost ready I decided to look into the other options for the file system.

After scouring Google for info, I've narrowed the choices down to EXT3, ReiserFS and JFS. Just to sum up what I've found with basic benefits / drawbacks:

EXT3 - Very stable. Most widely used and supported. Can be slow.

ReiserFS - Fast for systems with a bunch of small files (some people dispute this). Nobody really came out with strong support for this file system.

JFS - Very stable with good recovery / repair tools. Fast performance. Not widely used and community of supporters may be fading.

It seems to me that JFS is the best option from all of the different threads I have read. I installed the Kubuntu 8.10 RC on my secondary laptop with JFS and haven't seen any problems yet. Does anyone have any comments on file systems? Are there any caveots to using JFS? Are there better options?

---

### Post by aaronb on 2008-10-26
I use ext3 here as it has aways worked without issue and recovered well in power cuts. Plus upgrading to ext4 should be simple. And apparently ext4 has some cool new features.

ReiserFS 3.x was a good file system, but since Mr Reiser was jailed for murder I think development has stopped. In the past when I used SuSe linux I could not tell the difference in terms of speed.
[http://www.osnews.com/story/20233/Hans_Reiser_Sentenced_to_15-to-Life](http://www.osnews.com/story/20233/Hans_Reiser_Sentenced_to_15-to-Life)

ReiserFs was dropped by its main supporter in 2006.
[http://www.linux.com/feature/57788](http://www.linux.com/feature/57788)

The ReiserFS 4 was never accepted into the kernel.
[http://kernelnewbies.org/WhyReiser4IsNotIn](http://kernelnewbies.org/WhyReiser4IsNotIn)

---

### Post by undoIT on 2008-10-26
> **aaronb said:**
> ReiserFS 3.x was a good file system, but since Mr Reiser was jailed for murder I think development has stopped.

HellReiser ;)

---

### Post by bigbear2350 on 2008-10-26
ext4 is going to be marked stable in 2.6.28.

---

### Post by Bokonon on 2008-10-27
Take this as 100% opinion and from someone who has only dabbled in the various file systems, but without much in depth knowledge outside what you found in your own search.  I have done a few googles over the years and also look at the wikipedia.

[JFS]
JFS seems to be a bit flakey.  I have been using that for my big 1TB drives with my dvd iso files and am also using it as my /home mount partition on my laptop. 

Speed is good deleting and copying, but I get errors sometimes and have to drop to the console and do a manual fsck.jfs now and then to get the partition to mount.  Not so much now, but a PITA when it happens.

My last 2 HD deaths were on 100% JSF filesystems.  Probably bad luck and due to the fact that my backup drives are JFS mostly, but both drives died well before their mean time to failure.

[XFS]
Seems just as snappy as JFS to me and I have yet to have a major problem with any of my drives.  As I get new drives and have time, I am slowly switching all my JFS filesystems -> XFS.

I expect when I upgrade to the next distro, I will switch my /home partition to XFS

[ext3]
Rock solid, but slow on large file deletion and seems slightly slower on deleting lots of small files.  I prefer this for my / partition since it seems so rock solid.

I don't like it for /home or my .iso files since there is a noticeable slowdown.  Also, overall disk usage seems greater than JFS or XFS (i.e. I can store the same files on ext3 and it takes up slightly more space than JFS/XFS)

Minor inconvenience is the file system check on boot at times (every 30 boots???).  Certainly not a deal breaker and worth it for the stability, but my /home partition can take a long time to complete.

[reiser4]
Used this a long time ago and lost half my picture collection due to an error.  Cursed the file system to no end and never went back.  (FWIW, it probably was an early release of reiser4)

$0.02

---

### Post by Chuckels550 on 2008-10-27
My understanding is that for the system files you should use EXT3if you want to avoid boot issues when using Ubuntu.  For mythtv, many use the base file system, which is EXT3 for Ubuntu, for the system files and then a journalling file system for TV recordings because the files are so large.

ReiserFS was used as the base file system by SuSE and was dropped because of fears that there would be no support by the inventor -  Reiser has some hefty legal issues - something about his wife disappearing under suspicious circumstances.  Up until then, ReiserFS was well thought of.

I understood that JFS support in Ubuntu was not there and if a journaling file system was needed, XFS was the way to go.  I use XFS with the partition for my recordings in Mythbuntu because the file system handles large files so well.  Deleting a large file, like several Gigs of disk space, is instantaneous.  It works just fine for me.  For more information, check out the information 

See also [http://mythtv.org/docs/mythtv-HOWTO-24.html#ss24.2](http://mythtv.org/docs/mythtv-HOWTO-24.html#ss24.2) for more information.

---

### Post by undoIT on 2008-10-27
I have read a lot of bad things about running the OS on XFS. It does look good though for a secondary hard drive when working with large files.

Here are some links I found that compelled me to try JFS:

[http://www.linux.com/feature/119025](http://www.linux.com/feature/119025)

[http://brainstorm.ubuntu.com/idea/2147/](http://brainstorm.ubuntu.com/idea/2147/)

[http://www.dslreports.com/forum/r18916226-](http://www.dslreports.com/forum/r18916226-)

[http://bbs.archlinux.org/viewtopic.php?id=52005](http://bbs.archlinux.org/viewtopic.php?id=52005)

And here is a very informative wiki on JFS:

[http://wiki.archlinux.org/index.php/JFS](http://wiki.archlinux.org/index.php/JFS)

---

