---
title: "Adept doesn't show Version Upgrade?"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by 3rdear on 2008-11-18
I'm curious about upgrading my Kubuntu installation from Hardy to Intrepid, but Adept isn't showing any kind of version upgrade information.

Any help here?

---

### Post by Rohan Kapoor on 2008-11-18
Did you check out [http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Kubuntu%20Desktops%20(Recommended](http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Kubuntu%20Desktops%20(Recommended))

---

### Post by kde4-core-user on 2008-11-18
You need this command to start an upgrade to Intrepid with Adept Manager:

```
kdesudo 'adept_manager --dist-upgrade'
```

---

### Post by 3rdear on 2008-11-18
Ah ... 

Okay. Thanks folks. That helps explain why I'm not seeing it in Adept and what I can do to change that.

Still, I think I'll stick with Hardy until its support cycle is finished, especially since there are known issues with KDE 4 & Intrepid if using certain video drivers.

Now, if I could just get [my sound problem]("http://ubuntuforums.org/showthread.php?t=985762") fixed.

---

