---
title: "gcrontab not installable"
date: 2009-05-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yoasif on 2009-05-22
Hey guys... tried to install gcrontab -- not working for me. aptitude says the package is broken.

I submitted a bug report, but I'd like to provide more info or get a fix so it can be fixed. 

[https://bugs.launchpad.net/ubuntu/+source/gcrontab/+bug/379238](https://bugs.launchpad.net/ubuntu/+source/gcrontab/+bug/379238)

---

### Post by taavikko on 2009-05-23
confirmed, looks that nothing more than a dependency issue.

---

### Post by RainCT on 2009-05-23
GCrontab needs porting to GTK2. There's a patch with some of the work done at [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=515275](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=515275), but I've been unable to get it to build.

---

