---
title: "[SOLVED] Upgrade Edgy Eft to Heron question"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by afbase on 2008-07-29
I have a server with a bad cd player and edgy eft installed on it.  I cannot use a cd to do a fresh install, I'm not sure if I can upgrade to hardy heron because i just waited too long to install it.

It has an internet connection, and i have downloaded the hardy heron iso to my laptop (a different computer than my server).  Is there another way to upgrade my server?

---

### Post by Pumalite on 2008-07-29
Maybe this will work:
sudo sed -i 's/edgy/hardy/' /etc/apt/sources.list 
sudo apt-get update 
sudo apt-get dist-upgrade

---

### Post by afbase on 2008-07-29
```
Starting HTTP cache proxy server: wwwoffled
```


well i guess the installation has halted because it seems to be stuck at  this step. its been on this step for the past 20 minutes.

WWWoffled isn't that difficult to start up.  Any suggestions?

---

### Post by Sef on 2008-07-29
> Maybe this will work:
sudo sed -i 's/edgy/hardy/' /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade

Skipping releases breaks systems.  It would be better to upgrade to Gutsy Gibbon, then to Hardy Heron.

---

### Post by afbase on 2008-07-29
haha, ah crap well i suppose it is too late for that.  I've done all the steps.  and the computer seems to have hung on the step i just post.  It hasn't crashed, it just seems stuck on it.

If I Ctrl + C it, what would I do next?

I guess the better question is, what should I do next?

---

### Post by Pumalite on 2008-07-29
Sorry for my mistake. I was thinking of Dapper

---

### Post by afbase on 2008-08-01
It worked though.  That was the only hiccup i had during the upgrade.  After the upgrade, I just reinstalled WWWoffle.  

thanks again!

---

### Post by Pumalite on 2008-08-01
I'm glad you made it! I felt awful about my mistake.

---

