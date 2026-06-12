---
title: "Is anyone using Back In Time?"
date: 2009-12-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-12-05
I have just installed it on Stoned Lizard (daytime production OS).

I have 2 drives for my test platform sda (bootable) and sdb in an external enclosure.

Having more room on sdb I made an est4 partition there and gave the ownership to "Lazy Larry" for the folder created for the backup.

I can designate the entire partition but not the folder and am told that I do not have permission to write to the partition.

How do I straighten this out?

---

### Post by Gina on 2009-12-05
Perhaps group permissions would be a help :)

---

### Post by Toadinator on 2009-12-05
*nevermind, I just re-read what you asked. I was totally off.

---

### Post by ranch hand on 2009-12-05
I think I got it straight.  You have to be smart enough to change the permissions in /media so that you get the whole partition.

Now all I need to do is get the right file.  Going with just / does not seem to work, at least not judging by the results (largest file is 14 bytes - this is the bz2 file)

---

### Post by jfernyhough on 2009-12-05
I've had it running for the last eight months, works very nicely taking hourly snapshots of my /home/jf to a separate /home/jf.backup. I have narrowed things down a bit so it doesn't snapshot things like Firefox cache etc., but yeah - works absolutely fine, though I haven't tried to do it for the whole file system. I think that might be overkill, plus it'll probably end up hitting some recursion problems (if you backup / to /media/backup it will also try to backup /media/backup to /media/backup, and so on).

---

### Post by ranch hand on 2009-12-05
I am backing up to a partition formatted to ext4 with nothing else on it.  I usually do not back up this way but just copy my home folder to my backup partition.

Back in Time just looks like it ought to work well if I can just get enough brains to get it set up.

The way I am trying does not appear to work so I will have to narrow it down.

---

### Post by VMC on 2009-12-05
I use either Clonzilla or partclone.ext4 for my backups. I know Back in time keeps a more current backup.
You may have seen this, but here is a [link]("http://www.howtoforge.com/creating-backups-with-back-in-time-on-an-ubuntu-9.04-desktop") showing Back in time for Ubuntu 9.04, with pictures!

---

### Post by ranch hand on 2009-12-05
Thanks for that.  I think, looking at that, that I have done this right but it just doesn't handle what I asked it to do.

I will play with it more tomorrow when I am back on the testing drive.  I think I will pull up your link at that time to make sure I am hitting all the right steps.

---

