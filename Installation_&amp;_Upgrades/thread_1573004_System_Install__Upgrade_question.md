---
title: "System Install / Upgrade question"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by wbm on 2010-09-12
Hello, Ubuntu pretty much updates the system every 6 month. The general consent seems to be that clean installs are better than in place upgrades.
My question:
What would be the cleverest way to do clean installs every six month in regards to data?

It would appear clever to have one drive just for the system, and a separate drive just for data like pictueres, movies, music etc.. But, that still leaves the question of my Browser bookmarks, Tomboy notes, Evolution data and such sprinkled all over my system drive.

How are you guys handling this every six month?
Thanks!

---

### Post by mörgæs on 2010-09-12
Agree, a clean install is the best choice.

It is not mandatory to use every single release :-) If you have something that works, the easiest would be to upgrade when support is running out, thus skipping a lot of the releases.

The files you mentioned here are all contained in /home, but sometimes as hidden files. A good option is installing /home on its own partition.

---

### Post by wbm on 2010-09-13
> **mörgæs said:**
> Agree, a clean install is the best choice.

It is not mandatory to use every single release :-) If you have something that works, the easiest would be to upgrade when support is running out, thus skipping a lot of the releases.

The files you mentioned here are all contained in /home, but sometimes as hidden files. A good option is installing /home on its own partition.

Even if one skips a version or two in between, it would still remain the same situation/question when one does.

As far as I know /Home on a separate partition wouldn't really help much either due to incompatible permissions, preferences and settings that may or may nor work with a new install.

---

### Post by philinux on 2010-09-13
> **wbm said:**
> Even if one skips a version or two in between, it would still remain the same situation/question when one does.

As far as I know /Home on a separate partition wouldn't really help much either due to incompatible permissions, preferences and settings that may or may nor work with a new install.

I've had the same home now for 2 years and installed the new release every six months. 

There are no incompatible permissions as I recreate the same username and password each install. Preferences and settings are only text files. I've even used 32 bit then 64.

---

### Post by warfacegod on 2010-09-13
> **wbm said:**
> Even if one skips a version or two in between, it would still remain the same situation/question when one does.

As far as I know /Home on a separate partition wouldn't really help much either due to incompatible permissions, preferences and settings that may or may nor work with a new install.

Incompatible permissions can be fixed by using the chown command on the /home partition or drive. Do not, by the way, ever chown the entire filesystem. Bad idea.

Preferences and settings are unlikely to cause problems but, in the event they do, you can delete the offending folder/file. Ubuntu should create a new one if it wants something there.

I've been using a separate /home partition for over a year and the most I've ever had to do was chown.

---

