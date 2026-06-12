---
title: "Notify-OSD crashed"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by Bulettenschmied on 2012-04-29
Hi everybody,

first posting here, so - greetings to everyone around!

I posted this in the german Ubuntu forum, but as of right now didn't get any reply - maybe someone here can help me: After upgrading to Lubuntu 12.04 my Notify-OSD doesn't seem to work at all. That also caused the Lubuntu software center to crash (after uninstalling Notify-OSD it runs fine). Does anyone else have this problem and is there a way to fix it?

Best regards

---

### Post by Rex Bouwense on 2012-04-29
Welcome to the forums.  I have downloaded Lubuntu 12-04 but have not yet installed it.  For some reason that has been lost or forgotten, I always do a clean install after backing up all of my data.  Anyway, it sounds like something got messed up in the upgrade (which can happen) so if you want the Notify, then simply re-install.  You already know that you can un-install it to get the system working again.

---

### Post by Bulettenschmied on 2012-04-30
Hm, I guess that would have been too easy. After re-installing notify-OSD the software center indeed runs without problems. Alas, I still got no messages from my system.
Since I'm a rather newbie on Linux - how can I get an older version of the program (I mean the notify-OSD)? Somewhere somebody mentioned that this might solve the problem.

Best regards

---

### Post by josephmills on 2012-04-30
```
sudo apt-get install libnotify4 
```


then 

```
notify-send "hello World"
```

---

### Post by Bulettenschmied on 2012-04-30
> **josephmills said:**
> ```
sudo apt-get install libnotify4 
```


then 

```
notify-send "hello World"
```
Nope, nothing happens. Well, I guess I can live without a notification every now and then. But it would be nice to know, WHAT seems to be the trouble.
Thank you for your efforts!

---

