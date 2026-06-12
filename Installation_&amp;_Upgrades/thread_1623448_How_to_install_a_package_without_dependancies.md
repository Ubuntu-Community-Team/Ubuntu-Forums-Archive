---
title: "How to install a package without dependancies"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by dopefish7590 on 2010-11-16
Heya, I've searched around a bit for the answer to this question and most threads just got the response "Why the heck would you do that!?" so, to clear things up... I have installed VisualBoyAdvanceM via a forced architecture dpkg install to fix a bug vanilla VBA had (I am running 64-bit), and I made a link from where visualboyadvance's executable would usually be to this install, so it's acts the same way as the original program. But when I go to install VBAExpress to get GUI, it want's to install the vanilla VBA overtop of my already-working VBAM.

So, I would like to know how to install VBAExpress without VisualBoyAdvance included.

---

### Post by i.r.id10t on 2010-11-16
Get the debs w/ 
```
apt-get install -d <program name>
```

Then install alien
```
apt-get install alien
```

Then convert the .deb package to a .tar.gz file, extract and put the files where they need to be.

---

### Post by dopefish7590 on 2010-11-16
Thanks, that did it. :)

---

