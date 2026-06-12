---
title: "Best file system types for fresh 16.04 installation"
date: 2016-05-31
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2016-05-31
Bottom line (on top?): What is the most trouble-free type of file system for an Ubuntu 16.04 installation?

Greetings, Folks. 

In a [previous thread]("http://ubuntuforums.org/showthread.php?t=2326018") I described how my fresh 16.04 installation had been unstable from day-1.  It did not boot consistently.  Also that now it is not booting all the way up a a logins screen but rather to a series of messages starting with "No caching mode page found".  In the past 4 days that thread has been looked at many times and nobody has replied.  I think it's time to throw in the towel and just reinstall it all, since I have not yet committed much in this installation.  I have also begun to suspect my mix of file-system formats my be at the core of this.  The / (root) is ext3 while /home, /var and /tmp are ext2.  I had also created a /db01 partition (for database files) in ext3 format.

So here's my plan:
[LIST]
[*]Reboot from the Windows DVD and fix the MBR to Windows only.  This will lose the GRUB so I get a fresher start.
[*]Boot the GPARTED Live CD and reformat all my Ubuntu partitions in the same format. (This is at the crux of my question here.)
[*]Boot the Ubuntu CD and reinstall afresh.
[/LIST]

Based on my suspicion (the only one thus far not disproved) I'd like to reformat all my partitions to the same file-system type.  Which way to go?  I have seen some bad press about ext4 in various threads and other forums.  Would I be better off will everything in ext2 or ext3?  Or have ext4 bugs been addressed and now that is the way to go?

Thanks much for helpful advice.

---

### Post by The Cog on 2016-05-31
I would suggest using the default ext4 filesystem.
If you choose "something else" in the partitioning stage, you can go on to select the partition sizes and types there - no need for gparted first.
Though I don't see why your other choices might have caused problems.

---

### Post by oldfred on 2016-05-31
How old were the threads on ext4 issues?
That may have been true in 2009, but not really since it has been the Ubuntu standard since about then.

You should only use ext2 on small partitions as it does not have a journal. Recovery from a small partition works, where on a large partition, you need ext4 journal to be able to have a chance to recover.

---

### Post by ajgreeny on 2016-05-31
>  The / (root) is ext3 while /home, /var and /tmp are ext2. I had also created a /db01 partition (for database files) in ext3 format.Is there some good personal reason why you chose to separate /, /var and /tmp?

Doing so seldom adds any advantages to a standard desktop setup, though can be more useful for a server.

---

