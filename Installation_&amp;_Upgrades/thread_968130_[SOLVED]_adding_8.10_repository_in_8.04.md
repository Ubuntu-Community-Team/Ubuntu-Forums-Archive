---
title: "[SOLVED] adding 8.10 repository in 8.04"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by natirips on 2008-11-02
I've added Interpid Ibex's (8.10) repository in my Hardy Heron (8.04) to upgrage a game. However, now **it says there's 1210 upgrades** availible (which are **due to Interpid's repo**).

So I ask: **how smart would it be to update my system?**

Or should I remove the Interpid's repo from the sources.list since I'm done with the packages I wanted from it?

---

### Post by Partyboi2 on 2008-11-02
> Or should I remove the Interpid's repo from the sources.list since I'm done with the packages I wanted from it? I would recommend removing the intrepid repo's from your source.lists after you have got the package you want to avoid possible breakages.

---

### Post by natirips on 2008-11-03
I will as soon as I get home. Thanks.

---

### Post by Sef on 2008-11-03
Being careful when mixing repositories.   You can bork (totally crash) your system.

---

### Post by Dj TweeX on 2009-01-23
so im trying to add the repos to my sources.list.
but the file has no entries. should i be worried?
~~Gabe~~

---

### Post by ubuntu27 on 2009-01-23
> **Dj TweeX said:**
> so im trying to add the repos to my sources.list.
but the file has no entries. should i be worried?
~~Gabe~~

This usually happens when someone types incorrectly, eg. "souce" instead of  "source" or when typing the wrong directory.

Check your spelling.

If you are using Ubuntu (GNOME):

```
sudo gedit /etc/apt/sources.list
```

For More information about Source List, visit:

[https://help.ubuntu.com/community/SourcesList](https://help.ubuntu.com/community/SourcesList)

---

### Post by Dj TweeX on 2009-01-23
i just daid screw it & upgraded.
that worked btw thank you

---

