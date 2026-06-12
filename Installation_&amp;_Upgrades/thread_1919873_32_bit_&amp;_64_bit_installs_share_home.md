---
title: "32 bit &amp; 64 bit installs share /home ?"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by flemur13013 on 2012-02-03
Hi - 

I have 10.04 32 bit installed in its own / partition and /home on a different partition, on a 64 bit machine with 4G memory and plenty of disk space. I want to install 11.10 64 bit multi-boot with 10.04 (and win7).

I've shared /home with other installs (e.g. 32 bit Mint and openSUSE) with no real problems - **will it work for 32 bit 10.04 **and **64 bit 11.10 to share ****/home?**

TIA!

---

### Post by wolfen69 on 2012-02-03
Yes you can. See the answers [here]("http://superuser.com/questions/337715/can-debian-amd64-and-i386-share-the-same-home-folder").

---

### Post by oldfred on 2012-02-04
Many who say you can share the /home partition suggest different users/logins, so you are not really using the same data. The different versions can lead to issues. Software is designed for updating so going from older to newer should always work, but new version may add something that old version does not understand.

I prefer to leave /home inside my / (root). Without any data it is very small. I also move some hidden folders like the Firefox & Thunderbird profiles & Kmymoney data files that are in hidden files/folders. All my data then is in data partitions but settings in /home are with each install.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
Morbius1 uses bind, now:
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)
kansasnoob's sharing and Morbius1 use of bindfs older
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)

---

### Post by flemur13013 on 2012-02-05
I went with 64 bit 10.04 (NOT 11.10) and had no real problems, just some minor hassles.

FWIW notes: 
- The Daily/alternative install of 10.04 64 had multiple problems - no worky, so went with the standard release.
- 10.04 64 boots about 10 sec faster than 32 (~30 sec vs ~40).
- Video encoding with avidemux is maybe 25% faster (frames/sec).

> Many who say you can share the /home partition suggest different users/logins, so you are not really using the same data. I customize a lot of stuff and so want to share (reuse/keep) data - the only problem here was the older version of wine on the new install, easily fixed.  The other major items, like FF plugins&userChrome.css, and customized gnome and fluxbox setups all worked fine (except for pointing to the wrong firefox(s), which I installed in /home out of laziness).

---

