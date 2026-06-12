---
title: "JFS or Ext4?"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by akand074 on 2010-03-03
Hey guys, just a quick question. I read about each kind of file system, heres a quote; 

> **JFS** - IBM's **J**ournaled **F**ile**S**ystem- The first filesystem to offer journaling. JFS had many years of use in the IBM AIX® OS before being ported to GNU/Linux. JFS currently uses the least CPU resources of any GNU/Linux filesystem. Very fast at formatting, mounting and fsck's, and very good all-around performance, especially in conjunction with the deadline I/O scheduler. (See [JFS]("http://wiki.archlinux.org/index.php/JFS").) Not as widely supported as ext or ReiserFS, but very mature and stable. 

JFS seems to be a pretty good file system according to that, so my question is what benefits is there of using ext4 instead of JFS for my linux installation? If any? Also when I do a clean install of Ubuntu on my desktop (probably not until the release of lynx) I was going to try putting /, /home, /var, /boot, /tmp, and /usr on a separate partition. I was going to use ReiserFS for /var, but does anyone recommend a certain file system for the others? (Ext4, JFS, ReiserFS, XFS)? Because I know ReiserFS is supposed to be faster for a large amount of small files and XFS is fast for large files so would any other contain only small files / large files so that it would be beneficial to use those file systems? 

I guess the quick question got a little longer.. aha well any input would be great, thanks!

---

### Post by akand074 on 2010-03-03
bump, I'm in no real rush if there's no response this time I won't bother bumping again.

---

### Post by jrusso2 on 2010-03-03
I use JFS for / on all my systems.  I have never had an issue with it and its stable.

The only issues i have had was with ext 2,3 where I often lost data.

Ext 4 seems to have an issue with data loss but people seem to like it.  

The problem with somethings is prejudice against things NIH.  Not invented here.

---

### Post by Joe Ker1086 on 2010-03-03
I have never personally used JFS but I have used ext2, 3 and 4. EXT4 is by far the best of all of the EXT filesystems. I have never had any file loss with ext4 and there is no file fragmentation in ext4. Nothing against JFS though, but i think files can still fragment....

---

### Post by akand074 on 2010-03-03
> **Joe Ker1086 said:**
> I have never personally used JFS but I have used ext2, 3 and 4. EXT4 is by far the best of all of the EXT filesystems. I have never had any file loss with ext4 and there is no file fragmentation in ext4. Nothing against JFS though, but i think files can still fragment....

I've never had any problems with ext3 or ext4 either, has always been stable too. I was just wondering if there was any benefits to one over the other. I know the new ext4 allows for very large file sizes and double the amount of subdirectories as ext3 but its not like I have files that are 16TB anyways. I was going to stick with ext4 because I don't tend to fix what's not broken unless the benefits are worth it. I just don't really know the difference.

---

### Post by salemboot on 2010-03-27
Desktop filesystems shouldn't use too much CPU resource.  Huge files for example, DVD-Rom ISO's can lock down a file-system process.  There is an on-going post over at Phoronix.com about the disk-IO issues.  I just don't recall which post it's located in.

I do know that Phoronix benchmarked a few and Ext4 came out on top on moving data.  This is fine for file servers.  I think for the desktop operating system you need more moderation in that respect.  Scheduler problems perhaps indeed.

I'm experimenting with JFS myself right now.  One major leap for me was not using swap.  That reduces the amount of disk-IO by a fraction of 1%.  Although I hate using percentages.  

Another thing I've done over the years is keep the root and system related files away from the home directory.  I've used a 32GB root partition.  I was moving and relinking /var/cache/apt to the /home partition.  But that mass of archives stays under 5GB and usually doesn't grow by much. 

good luck:p

---

