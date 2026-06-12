---
title: "Update.... Insert Disk (Feisty Fawn Beta)"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by USAgent on 2007-03-29
Hey there,
As a new user to Ubuntu/Linux, I am currently very satisfied with my decision to ditch windows. However, I currently have a problem. Updates have been detected, and I would like to install them. Whenever I do, it says please insert the feisty fawn disk, which I do, but does not do anything about it. Someone the other day when I asked this question, said go into the synaptic repository and uncheck the cd option. I cannot find this item, can someone please help?

Thanks in advance.

---

### Post by taurus on 2007-03-29
You can do that from a terminal too.  Open a terminal, Applications -> Accessories -> Terminal, and edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line (or second one, whichever has the word CDROM in there) to comment it out.  Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

