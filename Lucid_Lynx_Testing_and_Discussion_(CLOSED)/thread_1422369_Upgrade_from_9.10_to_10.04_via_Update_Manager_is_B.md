---
title: "Upgrade from 9.10 to 10.04 via Update Manager is Broken"
date: 2010-03-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by frogotronic on 2010-03-05
Can't use the update manager to upgrade from 9.10 to 10.04.  Unmet dependencies from OpenOffice and Python.  See screenshot (attached).

- CH

---

### Post by xebian on 2010-03-05
10.04 is still under development.

It's like moving into a new house still under construction.

---

### Post by ratcheer on 2010-03-05
> **cement_head said:**
> Can't use the update manager to upgrade from 9.10 to 10.04.  


It worked for me. And, I know it has worked for others, too.

Tim

---

### Post by frogotronic on 2010-03-05
> **ratcheer said:**
> It worked for me. And, I know it has worked for others, too.

Tim

no OO bug?

---

### Post by tripolitan on 2010-03-05
If you are into pain and suffering, change your repositories to Lucid. Be sure to have a Karmic installation disk for re-installing Karmic, after you have realized the magnitude of this mistake.

Alternatively, wait at least a couple of months AFTER Lucid has been released and some bugs have been exterminated and do a full install. I have never had a successful distro "upgrade" in 11 years, except with Debian (pure).

---

### Post by sports fan Matt on 2010-03-05
I've had the alternate.  Every single upgrade since gutsy has gone flawless here.

---

### Post by kansasnoob on 2010-03-05
The first thing I notice is, "Running Partial Upgrade":

[http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

I have had fairly good luck rescuing mine using a chroot:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Sometimes if things are really hosed I'll start with:

```
apt-get install --reinstall ubuntu-minimal
apt-get install --reinstall ubuntu-standard
apt-get install --reinstall ubuntu-desktop
```

Sometimes that will present errors that give me a clue what do do next. Recently I had to purge the whole desktop metapackage and then install it again.

But I enjoy playing around, in reality it's faster to just do a fresh install, just not nearly as much fun :D

I like this quote:

> It's like moving into a new house still under construction. 

Alphas in particular are like a hard hat zone :p

---

### Post by kansasnoob on 2010-03-05
> **tripolitan said:**
> If you are into pain and suffering, change your repositories to Lucid. Be sure to have a Karmic installation disk for re-installing Karmic, after you have realized the magnitude of this mistake.

Alternatively, wait at least a couple of months AFTER Lucid has been released and some bugs have been exterminated and do a full install. I have never had a successful distro "upgrade" in 11 years, except with Debian (pure).

Great thought! I hadn't thought to mention checking the sources.list but that's essential. You could be working with partly Karmic/partly Lucid software sources!!!!!!!!!!!!!!

---

### Post by ratcheer on 2010-03-05
> **kansasnoob said:**
> Great thought! I hadn't thought to mention checking the sources.list but that's essential. You could be working with partly Karmic/partly Lucid software sources!!!!!!!!!!!!!!

Hmmm. I have not had that experience, either. When I am booted in Karmic, mine uses karmic sources, and when I am booted in Lucid, it uses Lucid sources.

Tim

---

### Post by nanog on 2010-03-05
There have been several broken packages in Oo.o -- you probably installed one of those. Try removing open office (you may have to force or purge), reconfiguring, and/or forcing install (see my sig).  This is exactly what is supposed to happen in development, btw.

---

### Post by sgage on 2010-03-05
The update-manager -d command has always worked for me. In fact, after a some time with Lucid, I just upgraded my Karmic installation, and it worked perfectly.

I guess there are just so many variables involved that it's hard to know what's going on sometimes.

---

### Post by peakshysteria on 2010-03-14
> **sox fan Matt said:**
> I've had the alternate.  Every single upgrade since gutsy has gone flawless here.

+1.Smooth sailing since Gutsy as well. Of course I've had the occasional bug, Ati troubles etc. But nothing serious. Nothing that I couldn't fix via the help of the forums.

> **sgage said:**
> The update-manager -d command has always worked for me. In fact, after a some time with Lucid, I just upgraded my Karmic installation, and it worked perfectly.

I guess there are just so many variables involved that it's hard to know what's going on sometimes.

Same command have always worked for me.

---

### Post by tripolitan on 2010-03-15
"Of course I've had the occasional bug, Ati troubles etc. But nothing serious. Nothing that I couldn't fix via the help of the forums."

You call that smooth sailing? :)

---

### Post by tripolitan on 2010-03-15
"Alphas in particular are like a hard hat zone "

They have been more like Biohazard zone for me :0

---

