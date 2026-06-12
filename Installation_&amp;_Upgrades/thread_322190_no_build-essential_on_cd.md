---
title: "no build-essential on cd?"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by bioboi69 on 2006-12-20
How is someone supposed to install build-essential when it's not on the CD. The whole point of my wanting to install build-essential is to compile my network drivers, therefore the repositories are useless!

---

### Post by Sef on 2006-12-20
From the terminal (Applications > Accessories > Terminal)

```
sudo aptitude update
```

```
sudo aptitude install build-essential
```

It will install some things on your computer and then ask you to put in your cd.

---

### Post by ciscosurfer on 2006-12-20
> **bioboi69 said:**
> How is someone supposed to install build-essential when it's not on the CD. The whole point of my wanting to install build-essential is to compile my network drivers, therefore the repositories are useless!I suspect you could do that following (btw, I've heard complaints similar to yours before, so this is not a unique issue) If you have another accessible partition on your drive that you can write to (perhaps Windows?), then you can download build-essential and then mount that partition (while using the liveCD) and copy over build-essential to compile your network drivers. 

Another option would be to download the DVD ISO, build-essential may already be there on that ISO.

I'm curious as well if anyone else has any further suggestions.

EDIT: Are wanting to do this from a LiveCD or from an Ubuntu CD in general?  If it's the latter, then follow Sef's advice.

---

