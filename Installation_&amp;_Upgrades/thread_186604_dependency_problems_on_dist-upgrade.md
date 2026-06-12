---
title: "dependency problems on dist-upgrade"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by flod on 2006-06-02
Hey guys,

I'm trying to upgrade to dapper on my laptop and there seems to be a problem.
I'm using the online repository, not a CD for upgrading, so I've changed in my sources.list all the breezys to dapper.
After 'aptitude update' I've run 'aptitude upgrade' (don't know for sure if it's necessary, but I wanted to make sure), which went w/o a problem, but when I'm trying to run 'aptitude dist-upgrade' I'm getting an unmet dependencies error for 'amarok-gstreamer' and 'openoffice.org-common'.
Does anyone know if there are still uncommited packages, or am I doing something wrong?
Another fact is that if I'm using 'apt-get' instead of 'aptitude' I don't get those errors anymore, but apt-get is removing a lot of packages including 'kubuntu-desktop', which doesn't seem to be right.

In case it makes any difference, my sources.list contains 'main restricted universe multiverse'.

Any thoughts?

Thanks in advance,
Florin.

---

### Post by ubuntu_demon on 2006-06-02
First look here :
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

---

