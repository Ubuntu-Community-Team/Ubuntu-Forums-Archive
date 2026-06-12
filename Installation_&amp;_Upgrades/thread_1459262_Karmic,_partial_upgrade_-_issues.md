---
title: "Karmic, partial upgrade - issues?"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by aaronp on 2010-04-21
Hi guys,

I came home to my PC (Karmic 9.10) offering me a partial upgrade. It didn't really seem like anything out of the ordinary except for the word 'partial' so I accepted it (stupidly).
It appears it has done some kind of half baked distribution upgrade and mucked around with things like Firefox (which is now Namoroka) and Thunderbird, as well as a handful of other packages.

I noticed in the terminal window when it was doing the upgrade it came across quite a few syntax errors or problems deleting folders etc. which was the first alert to me that something wasn't right.

Anyway, I've now read the sticky on this forum about partial upgrades (i.e. avoid them!) and the fact that they are usually a problem in testing/dev releases, not final releases.

I'm actually running the final Karmic release and not an alpha/beta Lucid version and this is my 'production' system, so I can't afford to lose data. I've got backups but wasn't intending on needing to use them!!

Unfortunately the sticky doesn't have a 'how to fix things if you're stupid enough to accept a partial upgrade without checking what it is first' section. 
Is anyone able to help me roll this back?

thanks
Aaron

---

### Post by zvacet on 2010-04-21
Let us see if you get any errors running 

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Post output here.

---

### Post by aaronp on 2010-04-22
> **zvacet said:**
> Let us see if you get any errors running 

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Post output here.

Thanks. Didn't get any errors (assumed you wanted me to press 'y' and get the updates offered)
After the upgrade Firefox told me to restart it which Idid, it is still calling itself Namoroka.

Output attached.

thanks
Aaron

---

### Post by zvacet on 2010-04-23
Sorry for late response.It look like everything is O.K. now.You didn´t get language packages,but you can live without them.

---

