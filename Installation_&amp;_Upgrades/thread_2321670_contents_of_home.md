---
title: "contents of /home"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by pfeiffep on 2016-04-23
I'm planning on a fresh install on Ubuntu Mate 16.04 LTS on the partition now housing Ubuntu 14.04 LTS; neither installation has a /home partition, and I'm the only user. 
I've been using Ubuntu Mate almost exclusively for the past month or so. 
I don't save data to /home as my data store is a NAS which provides the ability to share with 2 Ubuntu installs, 2 Windows installs, and a Mac. 
My interest in /home mainly is to preserve application settings (esspecially Thunderbiird rules and contacts) 
I'm seeking advice about:[INDENT]1) combining 2 /homes [/INDENT]
[INDENT=2]or
[/INDENT]
[INDENT] 2) abandoning Ubuntu 14.04 /home


[/INDENT]

---

### Post by oldfred on 2016-04-23
I do not suggest sharing /home. If versions are either identical or so far apart it may work, but most eventually end up with conflicts.

I keep /home inside my / with my Ubuntu installs.
But use a /mnt/data partition for all data, including some that is normally hidden in /home like .thunderbird & .mozilla. I move those into my data partition and edit profile.ini to find them. I started sharing like that with XP years ago using a NTFS data partition. 
I think I have the same profiles for the last 10 years. 

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

