---
title: "is there an apt-get log file?"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by pk386 on 2007-05-21
I just preformend an upgrade with 
```

apt-get upgrade
```

One of the libarys thats was upgraded broke a thrd party application that I'm using. (Mentorgraphics a Printed circuit board design program) 

How do I list what libary packages were upgraded when I did the last upgrade?
does apt have a log file? or is there another way?

---

### Post by earobinson on 2007-05-21
Synaptic has a history File->History, so I assume there is a log file somewhere, lets see if I can grep it.

Edit: found it /var/log/dpkg.log, note its actually a package log, so any installed updated removed etc package will be in that log

---

### Post by pk386 on 2007-05-21
cool now to sift trought the info 0_o


what is the best way to downgrade a package?
(or revert to the previous package?_

---

### Post by earobinson on 2007-05-21
thats what grep is for! ```
man grep
``` for more info.

---

### Post by pk386 on 2007-05-21
Yea I'm using grep lol still a lot of data...


what is the best way to downgrade a package?

---

### Post by earobinson on 2007-05-22
downgrading can be hard, you can uninstall the app, then go to /var/cache/apt/archives and see if you can find the correct deb file for the version your looking for, assuming you havent cleared your apt cache.

After you find the deb file you should be able to install it manually.

---

### Post by az on 2007-05-22
You can use synaptic to force a version of a package.  If the package deb is sill in /var/cache/apt/archives, you can get the choice of selecting that older version.  Whether or not synaptic will be able to install it or not depende on the dependencies.  If synaptic won't do it, it's because it is not a straightforward procedure...

---

### Post by earobinson on 2007-05-22
> **az said:**
> You can use synaptic to force a version of a package.  If the package deb is sill in /var/cache/apt/archives, you can get the choice of selecting that older version.  Whether or not synaptic will be able to install it or not depende on the dependencies.  If synaptic won't do it, it's because it is not a straightforward procedure...
Az, any idea if thats the same as just using dpkg, im pretty sure it is no?

---

