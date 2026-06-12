---
title: "Install Ubuntu dual HDD. OS on one and home on other. Help / tut ?"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by lordjubblydave on 2011-06-12
Hi all.

I am having troubles getting my box set up how i want it.

I  Have 2 HDD's i wish to install Ubuntu and Swap on the smaller one and  Have my Home folder with all my Docs/Music/Vids etc on the second HDD.

Is this possible ? or Sensible ?

Any thoughts or suggestions.

Thanks in advance

---

### Post by oldfred on 2011-06-12
It is doable and you can do it at least a couple of ways. I prefer to have a bootable system on every hard drive or at least have a full system on one drive and then have data on other drives.

If you format in advance you can just choose the /home partition on the other drive. (I have not done that, so not sure how to change drives in manual install, but seems possible).

Shows full install to second drive, not quite what you want, but shows manual process. Based on Maverick but process is similar with all versions, screens only change slightly.
Installing Ubuntu in Hard Disk Two (or more) Maverick 10.10
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)


I prefer to keep system partitions small. So I have several installs of Ubuntu my previous, my current & the next/beta/testing. But I have all my data in one partition. I find the actual hidden user settings are small and I just copy those I want to keep into each new /home and link in folders from my /data partition which sometimes is same drive and sometimes a different drive as I have installs on sdb & sdc. 

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Shared /data -see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

