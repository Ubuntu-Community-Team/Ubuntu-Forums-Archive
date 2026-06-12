---
title: "Gutsy Upgrade Problem"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by i-am-me on 2007-10-21
Right now I'm in the middle of upgrading to Gutsy. I've already done everything up to the package downloading, but as soon as the packages downloaded, the window closed and then that was it. Am I supposed to just install all the downloaded packages through adept since the channels are updated, click the version upgrade button again, or something else? This is Kubuntu 7.04 to 7.10 if that makes any difference.

---

### Post by Pumalite on 2007-10-21
[http://ubuntuforums.org/showthread.php?t=286599](http://ubuntuforums.org/showthread.php?t=286599)

---

### Post by i-am-me on 2007-10-21
My sources.list has already been updated the official way and the packages downloaded, but I'd have to install through adept if that's all it's (the official upgrade method) supposed to do.

---

### Post by Pumalite on 2007-10-21
Do this at the Terminal and you'll know for sure:
uname -a

You have to get something like this:

pumalite@pumalite-desktop:~$ uname -a
Linux pumalite-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
pumalite@pumalite-desktop:~$

---

### Post by i-am-me on 2007-10-21
That really doesn't say anything. It seems to only give the current kernel version and the last major update to it. Plus, the kernel was part of the downloaded packages. And just as a question, if I turn my computer off then back on, will the downloaded packages still be there?

---

### Post by Pumalite on 2007-10-21
That says everything. If you have that, you have your upgrade and you are fine.

---

### Post by i-am-me on 2007-10-21
Argh. I'm having serious problems. I get this every single time: 

```
*** stack smashing detected ***: /usr/bin/perl terminated
Segmentation fault (core dumped)
Setting up debconf (1.5.14ubuntu1) ...
*** stack smashing detected ***: /usr/bin/perl terminated
dpkg: error processing debconf (--configure):
 subprocess post-installation script killed by signal (Segmentation fault), core dumped
Errors were encountered while processing:
 debconf

```
What do I do?

---

### Post by ym4546 on 2007-10-22
I'm having this problem as well... the version upgrade window just closes... I haven't been able to find a solution.

---

### Post by wizzier on 2007-10-30
Encountered same "stack smashing" problem with Kubuntu Feisty to Gutsy upgrade. 
Upgrade on another Kubuntu system went smooth as silk.

---

### Post by Pumalite on 2007-10-30
At this point you guys should be seriously thinking of downloading an iso, saving /home and data and doing a clean install.

---

### Post by hacksaw on 2007-11-02
The upgrade from Kubuntu Feisty 7.04 to Gutsy 7.10 also crapped out on me when it got to installing  debconf.

The upgrade was via adept.Once it hung out to dry I found and killed the upgrade processes.

```
ps -ef | grep dist
```

```
root     14888     1  0 21:28 ?        00:01:01 /usr/bin/python /tmp/kde-root/adept_managerMaWy8b.tmp-extract/dist-upgrade.py --frontend DistUpgradeViewKDE --have-prerequists --with-network
root     14974 14888  0 22:44 ?        00:00:00 /usr/bin/python /tmp/kde-root/adept_managerMaWy8b.tmp-extract/dist-upgrade.py --frontend DistUpgradeViewKDE --have-prerequists --with-network

```

```
kill -9 14974; kill -9 14888
```

then ran

```
dpkg --configure -a
```

and then re-ran the upgrade processes

```
/usr/bin/python /tmp/kde-root/adept_managerMaWy8b.tmp-extract/dist-upgrade.py --frontend DistUpgradeViewKDE --have-prerequists --with-network
```

note: that the directory name adept_managerMaWy8b.tmp-extract and the process numbers may be different on you systems so check them.

The install then continued.:guitar:

I hope this is of some help.    cheers Hacksaw

---

### Post by rp142 on 2007-12-09
I gave up trying to upgrade from (Kubuntu) 7.04 to 7.10 after repeated failures.  Since I had a recent backup, I ran with a fresh install of 7.10 (deleted 7.04 partitions and created new freshly formatted partitions) which was trouble free until I went to install updates...  Now I have the the same seg fault when the updates attempt to install.

This problem does not appear to be limited to upgrades from 7.04 to 7.10.  There must be something about our installs that is unusual.  I have left all sources, etc at their defaults.

---

### Post by linhgb on 2007-12-12
I did an upgrade from feisty to gutsy on one machine (which started from edgy) & Adept crashed out very early on with the same error people here are getting, but I ran dpkg --configure -a then aptitude dist-upgrade a few times & it was all good. 

I then tried the same on another machine (started with dapper). Adept didn't crash until it was half way through & now it's unrecoverable. I'm going to do a fresh install on this one.

Both machines have the same source list & the upgrades were performed on the same day.

---

### Post by code-breaker on 2008-03-21
After several attempts at a clean install of Gutsy (which was 'encouraged' by a hardy rc5 upgrade gone wrong), I found this thread and it finally worked. 

dpkg --configure -a

...and...

aptitude dist-upgrade

...worked. Thank you.

---

