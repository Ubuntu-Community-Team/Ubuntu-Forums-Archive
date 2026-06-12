---
title: "lmfao I broke my Ubuntu"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by otherethe on 2010-11-12
I broke the update manager and i forgot what i did to brake it is the sad thing i know it was something i did how ever i was messing with my Nvidia drivers trying to find ways around the pink screen of death i been getting got this bug, didnt think nothing of it was sure a restart would fix it now here it is few hours later forgot what i done restarted and bug remains Copy pasting what it says


Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 59 in source list /etc/apt/sources.list (dist)'

Also maybe a little help lmfao Im also not sure were to report that at^^^^

I forgot i added some none sense to the .list file using the Terminal trying to force install the 195-glx nvidia dirvers not sure how to Delete this post

---

### Post by cchhrriiss121212 on 2010-11-12
It is telling you that line 59 of your sources list is wrong. So to fix it:
```
sudo gedit /etc/apt/sources.list
```
Then just delete line 59.

---

### Post by sikander3786 on 2010-11-12
Or if you can't figure it out yourself, post the output of

```
cat /etc/apt/sources.list
```

So we can do it for you ;-)

---

