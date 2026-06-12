---
title: "New motherboard + new SSD + old hard disk"
date: 2015-04-01
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2015-04-01
My motherboard died and I got a new one. In addition to that one I got also a 128 GB SSD hard disk.

I want to install a new system on the SSD. Was fast ;-)

I want to use as my home director for me /home/ronald  - BUT I want make a sym link to /media/ronald/e....../home/ronald

Whatever I try, the user ends up with no home directory and so I cannot login.

How would it work?

---

### Post by oldfred on 2015-04-01
I do not think you can symlink the entire /home. But it may just be the order of mounting. The system will not have mounted /media in time where /home would be mounted early in boot process.

But you can link all your data. I prefer to just have a data partition with just the standard folders like Documents, Video, Music etc and link each of those back into my /home.  I then am able to link that same data partition into all my test installs also.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by ELMIT on 2015-04-01
I think I solved great parts of it, by:

1. mount the old hard disk via fstab to /mnt/old-3T
2. I changed the passwd file from /home/ronald to /mnt/old-3T/home/ronald

That brought me back all most important things, like Thunderbird and Firefox.

Only thing I am still missing are all the icons in the launcher. I believe, they are setup with absolute paths and my extra programs path has not /mnt/old-3T/ prepend.

Is there a way to find them and correct them? Or am I wrong with my assumption?

---

