---
title: "Reinstall Ubuntu Possible?"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by jej2003 on 2008-01-02
So I think I screwed some thigns up with this install by installing multiple window managers (i.e. kde, kde4, gnome, xfce) and would like to knwo if there is a way to blow out everything and reinstall just xubuntu.  Anyone know how this can be accomplished? Or if there is a way to reinstall all the packages that are currently on the system that'd be good too.

---

### Post by ~LoKe on 2008-01-02
```
sudo dpkg -r gnome-desktop-environment kubuntu-desktop
```
Try that for starters.  Let's see what happens.

---

### Post by zvacet on 2008-01-03
[http://www.psychocats.net/ubuntu/purexfce]("http://www.psychocats.net/ubuntu/purexfce")

---

### Post by jej2003 on 2008-01-03
Ok, that is done, it just seems that some times XFCE is a bit unstable now (i.e. when goign to changing user when using Synaptic it has frozen 4 of last 5 times).  Is there a way to reinstall xubuntu as well?

---

### Post by zvacet on 2008-01-03
```
sudo apt-get inistall --reinstall xubuntu-desktop
```

---

