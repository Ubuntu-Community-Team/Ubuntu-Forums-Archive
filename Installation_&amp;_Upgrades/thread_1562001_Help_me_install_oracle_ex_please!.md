---
title: "Help me install oracle ex please!"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by xvanadiumx on 2010-08-27
Ok, im new to linux, I only just installed ubuntu... so far am very impressed... 

Im trying to install oracle 10g express edition and im getting this error:

You have insufficient diskspace in the destination directory (/usr/lib) to install .... bla bla bla you need 1.5gigs of space.

this is df -k:
/dev/loop0             8813300   6306304   2059304  76% /
none                    767668       284    767384   1% /dev
none                    772040      1476    770564   1% /dev/shm
none                    772040        88    771952   1% /var/run
none                    772040         0    772040   0% /var/lock
none                    772040         0    772040   0% /lib/init/rw
/dev/sda5             19535008  13172864   6362144  68% /host
none                   8813300   6306304   2059304  76% /var/lib/ureadahead/debugfs
/dev/sda6             19535008  18820124    714884  97% /media/Music
/dev/sda1              9767488   9659528    107960  99% /media/8C68E0EB68E0D4CC
/dev/sda7            107450720  98291920   9158800  92% /media/Media & Games


how do I fix this problem... did I install ubuntu wrong? any ideas?

---

### Post by Waappu on 2010-08-29
Hi,

As I understand you have 1,9 GB free on / and folder usr is under root.
And also your /tmp folder is under root, so I see you have quite small space.

Use
```
df -h
```

---

### Post by W00ster on 2010-08-30
I do not use the express version but if it uses the same installer as the normal versions, just run:
./runInstaller -IngoreSysPreReqs

---

### Post by Waappu on 2010-08-30
Hi,

XE have deb package. I think it us best use that. Here is few quides
[http://www.debian-administration.org/articles/430](http://www.debian-administration.org/articles/430)
[https://help.ubuntu.com/community/Oracle10g](https://help.ubuntu.com/community/Oracle10g)
[http://www.oracle.com/technetwork/topics/linux/xe-on-kubuntu-087822.html](http://www.oracle.com/technetwork/topics/linux/xe-on-kubuntu-087822.html)

And I still think OP have quite small disk.

---

