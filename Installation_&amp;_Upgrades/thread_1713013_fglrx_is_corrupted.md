---
title: "fglrx is corrupted"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by Reginthorn on 2011-03-23
Hey here is a picture of my problem! [IMG]http://www.imageurlhost.com/images/coor3n36dua75zawjm.png[/IMG]

---

### Post by zvacet on 2011-03-25
First,you don't have to type 
```
sudo -i
```

just put sudo in front of command and you are good to go.If you use **sudo -i** you don't have to type **sudo** because you are root already.Now,type in terminal

```
sudo dpkg --configure -a
```

---

