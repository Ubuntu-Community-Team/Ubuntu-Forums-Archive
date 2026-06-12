---
title: "skype in oneiric error start after distr upgrade"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by masuch on 2011-10-19
I cannot start skype after distribution upgrade to oneiric. I have this issue on 5 different ubuntu instances.

error:
skype: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory

ls -l `sudo locate libXss.so.1`
lrwxrwxrwx 1 root root    15 Oct 14 00:24 /usr/lib/x86_64-linux-gnu/libXss.so.1 -> libXss.so.1.0.0
-rw-r--r-- 1 root root 14480 Aug 11 20:19 /usr/lib/x86_64-linux-gnu/libXss.so.1.0.0


Does anybody know how to fix it ?
thanks,

---

### Post by masuch on 2011-10-20
Sorry to asked already solved:
[http://ubuntuforums.org/showthread.php?p=7892106](http://ubuntuforums.org/showthread.php?p=7892106)

simple solving:
sudo apt-get remove --purge skype
sudo apt-get install skype

---

