---
title: "synaptic reinstall"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by DCalabrese on 2010-07-23
[SIZE=3]Hi:  A programmer who relies entirely on code [now on vacation] worked on our Ubuntu 10.4.  Now there is no synaptic on the machine.  How do I reinstall it?   Thanks Chris[/SIZE]

---

### Post by wojox on 2010-07-23
Synaptic is a graphical front-end to apt. Try

```
sudo apt-get update; sudo apt-get install --reinstall synaptic
```

You need to to do this in a terminal. 

Alt+F2 

Type *gnome-terminal*

---

