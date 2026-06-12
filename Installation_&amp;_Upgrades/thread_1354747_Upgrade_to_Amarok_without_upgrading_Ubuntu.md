---
title: "Upgrade to Amarok without upgrading Ubuntu"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by kuriharu on 2009-12-14
Hey all,

I'm running Intrepid and I don't want to upgrade just yet. Thing is, I want to upgrade Amarok (I'm currently running 1.4 and the latest is 2.2.1 I think). 

Their support says I can run Neon but doesn't say how to install it. Compiling the latest version errors out (ah, my earlier Linux days come back to mind). 

Anybody know how to upgrade Amarok without 
a.) upgrading to Karmic yet and 
b.) screwing up my system?

Thanks!

Oh yeah, "apt-get install amarok" just returns "amarok is already the latest version".

---

### Post by howefield on 2009-12-14
> **kuriharu said:**
> Their support says I can run Neon but doesn't say how to install it.

Yes it does, use the repository as explained

[http://amarok.kde.org/en/node/482](http://amarok.kde.org/en/node/482)

Remember that this is a nightly build, and therefore may not be stable.

Or try adding the repository for the stable version, 

[http://amarok.kde.org/wiki/Download:Kubuntu#Staying_current](http://amarok.kde.org/wiki/Download:Kubuntu#Staying_current)

---

### Post by kuriharu on 2009-12-14
You're right, I just re-read the line below adding the repository. I'm a total idiot. My bad. Thanks for pointing it out to me (*embarrassed grin*)

---

### Post by kuriharu on 2009-12-14
Okay, so I added this repository, just like it says:

deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) hardy main

Then I ran apt-get update. It runs without errors. Then when I go

apt-get install amarok-nightly 

like it says to, I get that it can't find that package. I did an apt-cache search amarok but didn't find anything resembling this. Any clues?

---

### Post by kuriharu on 2009-12-14
OH yeah, the "staying current" instructions don't work, either. I substituted "karmic" with "intrepid" like it says to, and it can't find the packages on apt-get update.

---

### Post by howefield on 2009-12-14
Did you do an update prior to trying to install, either by reloading the packages in Synaptic or from terminal

```
sudo apt-get update
```

Also I'm a little confused, you mention both Hardy and Intrepid, which are you using ?

---

### Post by kuriharu on 2009-12-14
Thanks for the help.

I did run apt-get update.

I'm running intrepid, but one of the support sites mentions Hardy and only lists that and not intrepid, so I may have copied that line-for-line.

---

