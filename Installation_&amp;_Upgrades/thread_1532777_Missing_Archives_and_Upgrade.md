---
title: "Missing Archives and Upgrade"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by cosmicsteve on 2010-07-16
It seems as though something has gone rather screwy with my network connection in ways I don't understand. I am running 64 bit 9.10, and am trying to get some new software through the repositories. However, it seems as though my computer is failing to find some of the Ubuntu repositories for some reason, even though my network connection is just fine. 

I tried to upgrade, but this connection also keeps me from upgrading- it tells me to check my connection as it cannot download the release notes. 

I am not sure how this could have happened or what to do to fix it. I am no wizard, but this isn't my first Linux rodeo either. Any help out there?

---

### Post by zvacet on 2010-07-17
System>admin>software sources> change server to main( or other then one you are using now).Post output of 

```
cat /etc/apt/sources.list
```

just in case.

---

### Post by cosmicsteve on 2010-07-17
So it turns out I figured out what the problem was: it seems as though the Ubuntu repositories didn't like a proxy server I set up. Turning that off made things work again!

---

