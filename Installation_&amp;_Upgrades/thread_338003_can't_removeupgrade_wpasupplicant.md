---
title: "can't remove/upgrade wpasupplicant"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by markster23 on 2007-01-13
hey.. i'm using kubuntu edgy and got an update with adept-notifier for wpasupplicant.. when i tried to upgrade it, it wouldn't install the newer version, and now it's stuck saying it's a broken pacakge or something.. won't let me upgrade any other packages or anything.. here's the output when i try to manually remove it with apt-get or dpkg..

```

markthefart@delld3000:~$ sudo dpkg --remove --force-depends --force-remove-reinstreq wpasupplicant
(Reading database ... 137863 files and directories currently installed.)
Removing wpasupplicant ...
dpkg: error processing wpasupplicant (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 wpasupplicant
markthefart@delld3000:~$  

```any ideas ?? thanx :D

---

### Post by markster23 on 2007-01-13
ahhh figured it out :P

---

### Post by brazzmonkey on 2007-01-15
would you mind sharing how you to proceed ? many people (including me) seem to face this issue.

---

### Post by brazzmonkey on 2007-01-15
alright, solution is given here [http://www.ubuntuforums.org/showthread.php?p=2009165](http://www.ubuntuforums.org/showthread.php?p=2009165) by in_flu_ence

---

