---
title: "Upgrading to Ubuntu 7.04"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by wow20 on 2007-05-19
Hi

I was trying to upgrade to Ubuntu 7.04 but while trying to upgrade this error ocurred:

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://my.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

i tried again and it still didnt work and im pretty sure that my internet is working fine.
what should i do?

---

### Post by aysiu on 2007-05-19
I'd try a different mirror:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by zek725 on 2007-05-19
Ubuntu servers were probably busy. You can upgrade from an ISO alternate install image downloaded, though.

---

### Post by arvevans on 2007-05-19
I had the same problem.  Changing mirrors does not fix the problem.  Various apt-get actions will not fix the problem.

It is usually the last two files that are not downloaded, and this blocks continuation of the update process.

While many people suggested things that did not help (thanks anyway), I was never able to overcome this situation.

Apparently this is a bug in the UPDATER programs.  

I finally gave up...backed up my /home directory onto another computer...and then did a fresh install (with formatting) to get to Ubuntu 7.04.  After that I copied my old /home files from the backup system.  This worked, but of course I lost all my main system configurations that were established in /etc/***, and had to re-install the other programs that were not automatically installed from the 7.04 CD.

Good luck,

Arv
_._

---

### Post by aysiu on 2007-05-19
There are also a couple of other potential fixes [here](http://ubuntuforums.org/showthread.php?p=2025694#post2025694) if trying a different mirror doesn't work.

---

