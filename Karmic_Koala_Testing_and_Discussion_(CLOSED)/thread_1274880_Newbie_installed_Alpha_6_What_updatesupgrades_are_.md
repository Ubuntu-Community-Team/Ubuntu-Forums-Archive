---
title: "Newbie installed Alpha 6: What updates/upgrades are safe?"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bridgetothesun on 2009-09-25
My update manager is chock full of updates/upgrades? Which are safe and which should I avoid? Which are imperative?

Thanks!

---

### Post by P4man on 2009-09-25
None are safe. The alpha you are using isn't safe. Though it hopefully won't happen (again), any upgrade could break your system, thats why its called alpha and is "for testing only".

---

### Post by moviemaniac on 2009-09-25
If your system works then right now I wouldn't update at all and wait an additional few days until the beta rolls on. There's a few boot-related bugs right now I hope will be fixed until then and there's currently also a huge amount of changes going on to usplash/xsplash/gdm I don't want to be caught in the middle of.

---

### Post by nhasian on 2009-09-25
i recommend backing up your root partition with clonezilla.  then feel free to do the update.  most likely it will work fine.  in the event that the update breaks your system, you can quickly restore your partition in like 5 mins.

---

### Post by philinux on 2009-09-25
> **bridgetothesun said:**
> My update manager is chock full of updates/upgrades? Which are safe and which should I avoid? Which are imperative?

Thanks!

Avoid any partial upgrade. Read the stickies on this forum.

I always use this during the development cycle.
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by Sophont on 2009-09-25
> **bridgetothesun said:**
> My update manager is chock full of updates/upgrades? Which are safe and which should I avoid? Which are imperative?

Thanks!

What P4man said.

Plus - you want to cherry-pick updates? I think you underestimate the update-rate. There's easily double digit number of updates most days and sometimes > 100.

There's a couple of things people can do to avoid worst breakage most of the time - but mostly you have to just get the upgrades (avoid partials in Update Manager) and hope they work with your system. And know in advance how you can recover when (not if :-) ) things go south (which is likely to happen once in a while even if you are careful).

If you're not ready for some breakage then you're not ready for a "testing" phase.

---

### Post by gjoellee on 2009-09-25
If you are a newbie that wonders which updates are safe and not, I won't recommend you using Ubuntu 9.10 Karmic Koala before the final version is released. 

It is still in Alpha (soon beta) and should not be used by anyone who don't want to test it, or don't know how to in example fix common issues.

---

### Post by dadedo123 on 2009-09-25
If Partial updates are dangerous and could damage our systems, then why do they put them? :p

---

### Post by philinux on 2009-09-25
> **dadedo123 said:**
> If Partial updates are dangerous and could damage our systems, then why do they put them? :p

It's not that they put them in it's just the way update manager works and the fact that some packages get held back during the development cycle.
I always use this
sudo apt-get update && sudo apt-get dist-upgrade

For more info see here.
[https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases#Testing%20and%20Working](https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases#Testing%20and%20Working)

---

### Post by bridgetothesun on 2009-09-25
Thanks. I'll wait till beta. I did upgrade a few programs yesterday. If I start experiencing issues, will upgrading to Beta possibly fix those?

---

### Post by philinux on 2009-09-25
The whole idea of running a development release such as karmic, is to test and report bugs. Some could be hardware specific. 

I'm running karmic on my second internal hard drive. If it breaks I report bugs etc and either fix or or wait for a fix.

If we all waited for this or that what would be the point in having karmic running.

---

### Post by solitaire on 2009-09-25
Ubuntu's Writ of Alpha OS's

All updates are safe, 
except the unsafe updates 
(which may be safe or my be unsafe.)

But it's safe to say
that the safe updates
are safe to install
and the unsafe updates 
are also safe to install

...unless you wait for a beta 
when all the unsafe updates will be safe...
unless they are unsafe.... >_<


If you want safe .... wait till Beta
unless you like unsafe ... then go with Alpha-6 ^_~

lol!!

---

### Post by ranch hand on 2009-09-25
> **bridgetothesun said:**
> Thanks. I'll wait till beta. I did upgrade a few programs yesterday. If I start experiencing issues, will upgrading to Beta possibly fix those?
Probably.  And cause other problems.

That is what testing is for, find the bugs BEFORE the release.

---

