---
title: "Best filesystem for laptop"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by yamla on 2006-06-05
I'm hoping to pick up a laptop later this month and of course will be primarily running Ubuntu 6.06 on it.  I'm wondering, what is the best file system for a laptop?  I'll be doing a fair amount of software development so I'll tend to be looking at a fair number of smaller files.  I obviously want a journalled file system but I understand that some make different use of disk caching than others.  XFS, for example, seems to cache changes and dump them out to disk only once every 30 seconds or so (iirc).

So, which file system would likely be the best choice for me with the goal of minimising actual disk usage?  What mount options are likely to help?

On various desktop systems around here, I use ext3, reiserfs (3, not 4), and XFS (for my PVR computer).

---

### Post by xXx 0wn3d xXx on 2006-06-05
I would recommend ext3. It's as stable as a rock and it has never failed me. If you want a little more speed but less stable, use reisersfs. JFS and XFS are mainly used for servers.

---

### Post by HankB on 2006-06-05
I'm not voting because I don't have a well researched answer.

I have however been running reiser on my laptops for some years now and have not experienced problems. 

It looks like breezy uses reiser3 based on messages on kern.log (3.6) even though reiser4 tools are installed.

I don't know what dapper installs because all of my PCs are upgrades from dapper.

I don't know if any of the other JFSs are better, but reiser has been good enough.

-hank

---

### Post by ubuntu_demon on 2006-06-05
I voted reiserfs.But I'm suggesting a seperate reiserfs partition where you can do the development with all those small files.

[http://en.wikipedia.org/wiki/Reiserfs](http://en.wikipedia.org/wiki/Reiserfs) :
> 
Performance
Compared to ext2 and ext3 in 2.4, when dealing with files under 4k and with tail packing enabled, ReiserFS is often faster by a factor of 10&#8211;15. This is of great benefit in Usenet news spools, HTTP caches, mail delivery systems and other applications where performance with small files is critical.


So it's probably faster if handling lots of small files is your primary concern.

My suggestion. You should make at least 4 partitions. Something like :
/ ext3
/home ext3
/mnt/software_development reiserfs
swap

---

### Post by Chickenmonger on 2006-06-05
Back when I used Slackware on an old Pentium 133, ReiserFS helped out a lot when accessing all the small files Swaret used for package management. 

Nowadays, I'd say ext3. I believe ReiserFS is a bit more aggressive with journaling, so it would be a worse choice for a laptop.

ubuntu_demon's suggestion sounds like a good compromise.

---

### Post by SoloSalsa on 2006-10-22
I'd make something up.  JFS-not.  See, JFS has the least CPU usage, fast mount time, and is pretty good with tiny bits.  But I wouldn't care for the journal.  My laptop NEVER has a power failure.  If it's plugged in, and something goes wrong, it instantly switches to battery power.  And, I'm using Xubuntu, so I'll save even more CPU.  If only there were a system as CPU-light as JFS, minus the journal...  For me, at least.

---

