---
title: "64 bit: Icedtea6- plugin just does not work, grey boxes where applet should appear."
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-03-28
Had to uninstall and use the sun-java6-plugin which works but not great.

The icedtea plugin fails also on java.com.

---

### Post by Chemical Imbalance on 2009-03-28
On Jaunty, the regular 64bit mozilla plugin is available and works perfectly for me.  I also had problems with icedtea with text clipping and general incompatibility.

---

### Post by zenarcher on 2009-03-28
I had to dump the icedtea plugin, as well.

Cheers,
zenarcher

---

### Post by Chemical Imbalance on 2009-03-28
I'm perplexed as to why they make icedtea the default instead of the regular sun plugin when clearly the icedtea doesn't work.

---

### Post by philinux on 2009-03-28
> **Chemical Imbalance said:**
> On Jaunty, the regular 64bit mozilla plugin is available and works perfectly for me.  I also had problems with icedtea with text clipping and general incompatibility.

Something other than sun-java6-plugin?

---

### Post by Chemical Imbalance on 2009-03-28
> **philinux said:**
> Something other than sun-java6-plugin?

Not that I know of.  It is the official sun plugin.

---

### Post by philinux on 2009-03-28
> **Chemical Imbalance said:**
> Not that I know of.  It is the official sun plugin.

Yes build 12, /usr/lib/jvm/java-6-sun-1.6.0.12/jre/lib/amd64/libnpjp2.so. The latest is build 13. Hope is gets updated or backported soon.

---

### Post by Chemical Imbalance on 2009-03-28
Here's a thread that *might* be helpful:

[http://ubuntuforums.org/showthread.php?t=1013658](http://ubuntuforums.org/showthread.php?t=1013658)

oops, you already posted in that :lolflag:

---

### Post by Polygon on 2009-03-28
icedtea has never worked for me. Just ditch it and install the 64 bit version of sun java.

---

### Post by novafluxx on 2009-03-28
> **Polygon said:**
> icedtea has never worked for me. Just ditch it and install the 64 bit version of sun java.

Same here...

I'd love to give the OpenJDK stuff a shot, but it just doesn't work for me, doesn't do what I want...

pogo.com, yahoo games, etc

So I just stick with Sun's Java for my 64-bits :)

---

### Post by Nullack on 2009-03-28
I created a bug on this topic in LP. Can anyone be sure this used to work in Intrepid? If so, we could tag the bug with regression-potential.

---

### Post by Chemical Imbalance on 2009-03-28
It didn't work on intrepid for me either.  I just used my 32-bit netbook for java stuff before Jaunty's inclusion of the sun plugin for 64 bit.  Intrepid was my first move to 64 bit though.

---

