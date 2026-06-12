---
title: "Can't start add/remove tool"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by tinhlx on 2008-03-30
hi all,
i'm using ubuntu 7.10, i can't start add/remove tool and when i try to start, it don't say anything. anybody help me.
thanks
tinhlx

---

### Post by Pumalite on 2008-03-30
System>Administration>Software Sources. Make sure all repositories are ticked. Reload. Then try again.

---

### Post by tinhlx on 2008-03-31
thanks Pumalite, i tried follow your instruction, but it still doen't work

---

### Post by zvacet on 2008-03-31
Check your internet connection.Can you browse?

---

### Post by tinhlx on 2008-03-31
yes, i can browse

---

### Post by prismpirate on 2008-03-31
I think this might work

Open Terminal by going to:

Applications > Accessories > Terminal

Copy this into the terminal:

```

sudo apt-get update

```

Try if it works

---

### Post by zvacet on 2008-03-31
System>Administration>Software Sources>change server.If it is on main put it to some local near you,or if it is on local put it on main.Reload and try again.

---

