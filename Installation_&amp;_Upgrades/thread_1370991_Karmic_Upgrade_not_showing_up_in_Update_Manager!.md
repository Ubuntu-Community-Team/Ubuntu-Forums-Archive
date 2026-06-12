---
title: "Karmic Upgrade not showing up in Update Manager!"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by sixstringtiger on 2010-01-02
Running Jaunty. For the life of me I can't get the Karmic 9.10 "update available" to show up in the update manager. I've enabled "Normal Releases" in the software sources and I've seen every update available since Hardy (I started with Hardy, then upgraded to Intrepid and Jaunty so far). I always get notified of typical security updates, etc and have it checking once per day.

The only weird thing I can think of is that I installed Ubuntu Studio's packaged on top of my normal Jaunty install. Would this affect things?

How can I "make" it see Karmic being available? Update Manager is the only way I know to upgrade. Is there a terminal method using apt or something?

---

### Post by ugm6hr on 2010-01-03
This will probably work:
[http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Servers%20%28Recommended%29](http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Servers%20%28Recommended%29)

However, it is often sensible to do a fresh install; it just ensures all the cobwebs from previous versions are removed completely.

Consider installing using a separate /home partition - this makes doing future fresh re-installs very easy (and means you don't even have to back anything up).

---

### Post by sixstringtiger on 2010-01-07
Thanks -- that terminal command worked perfectly! I appreciate the reference -- don't know why I didn't stumble across that.

My laptop is happy now.

---

