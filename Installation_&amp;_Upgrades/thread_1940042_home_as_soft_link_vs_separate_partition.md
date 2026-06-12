---
title: "/home as soft link vs separate partition"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by kamelie1706 on 2012-03-12
hi,

i want to move my /home directory to another drive.

I understand you can make a dedicated partition but is it possible to just move the home directory and create a soft link to it?

the hardrive I want to move the directory is automatically mounted at startup on /media/disk1. hone directory would be /media/disk1/home.

is it working? if yes what is the advantage of dedicated partition compare to this method?

probably not searching on right words as I did not find any information about the managing home directory that way ...

---

### Post by oldfred on 2012-03-13
If it is an external drive you may have some issues. You cannot mount it as /media/xxxx but as /home. And you edit fstab to mount the /home partition as /home.

# MoveHome.txt
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

But another choice is just to move data to another partition. I do this and have my entire system with /home in 20 to 25GB / (root) installs. I use links and others suggest bind. Bind is better if networking or installing different systems. But with only Debian based installs on one system links work just fine.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Another way to share:
Morbius1 uses bind, now:
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)

---

### Post by kamelie1706 on 2012-03-13
Hi,
 
Thanks for the very detail answer. I understood the best way was to have a separate partition (read already a lot about that). My question was more is could I manage it **without a separate partition** just by moving/linking  the directory to an existing disk (in my case internal). 
 
From what I read answer is no :-)

---

### Post by Morbius1 on 2012-03-13
From the links towards the botttom of oldfred's post that you apparently did not read the answer is yes.

---

### Post by kamelie1706 on 2012-03-13
Ok .... I have been reading to fast after long working day .... I will read more carefully then.

Thanks!

---

