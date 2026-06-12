---
title: "No nice splash screen after update and ext4 or btrf ?"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Hagar55 on 2010-10-10
I upgraded my install on the desktop to 10.10 and instead of the nice splashscreen I get something horrible with maverick meerkat in simple font....what went wrong ??

I'm thinking of reinstalling the linux install on my laptop.
Right now it's still on ext3 and it's already an ubuntu that's been upgraded twice and things are starting to simply not work anymore.

So if I install 10.10 afresh, what should I go for, ext4...wich should be nice and stable, or go for the newest of the litter and try btrf ?

---

### Post by mörgæs on 2010-10-10
Yes, a fresh install would be a good option. 

The file system does not matter as much as commonly believed. If you want some opinions, there are posts here:

[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by psusi on 2010-10-10
Ext4.  Btrfs is simply too unstable yet.

---

### Post by MeanEYE on 2010-10-10
> **Hagar55 said:**
> I upgraded my install on the desktop to 10.10 and instead of the nice splashscreen I get something horrible with maverick meerkat in simple font....what went wrong ??

I'm thinking of reinstalling the linux install on my laptop.
Right now it's still on ext3 and it's already an ubuntu that's been upgraded twice and things are starting to simply not work anymore.

So if I install 10.10 afresh, what should I go for, ext4...wich should be nice and stable, or go for the newest of the litter and try btrf ?

Hm, if you happen to have nVidia drivers installed then splash screen is not showing nicely because of that (probably). If you ask me, I'd go for ext4. This file system is being used for some time now so you can count on it as stable file system. To be honest I've never had any problems with any version of ext file systems. There are some faster file systems out there but I don't know... I kind of grew to like this one. Also ext4 supports home folder encryption, it's faster than ext3 and all sorts of nice things.

---

### Post by psusi on 2010-10-10
> **MeanEYE said:**
> Also ext4 supports home folder encryption

No, it doesn't.

---

### Post by Hagar55 on 2010-10-11
I do have an aging FX5200 installed (entire system is a bit of a dinosaur really...).

---

### Post by mörgæs on 2010-10-11
This is also my screen card, and it works well in 9.10 without any modifications. Have not tried on the newer versions.

---

### Post by bingus on 2010-10-12
I have the same problem. It sure is one ugly splash screen! Everything still boots up OK at least.

I was also thinking about doing a straight install rather than an upgrade. It never seems to work properly, on any distribution.

---

### Post by bingus on 2010-10-12
Double post, sorry

---

### Post by drs305 on 2010-10-12
For users with Nvidia drivers, see this thread:
[http://ubuntuforums.org/showthread.php?t=1592442]("http://ubuntuforums.org/showthread.php?t=1592442")

Startup-Manager seemed to be an easy fix. I also tried the fix linked to in Post # 4 and it worked although I reversed it after I saw it was a valid fix even in Maverick.

---

