---
title: "Quick upgrade question."
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Chowderpilot on 2007-04-19
I have been running the 7.04 Beta for a while, and when I do fetch updates in Adept Manager or run the gksu "update-manager -c" command it says my system is up to date. I have installed small updates along the way. I assume I am running the released version however, I want to ensure that I have the release version of Feisty, is there a command I can run or a way I can tell that it is indeed the release version? 

Thanks everyone.

---

### Post by singlemalt on 2007-04-19
To upgarde just open a terminal window

sudo apt-get upgrade
sudo apt-get update

---

### Post by mattack on 2007-04-19
> **singlemalt said:**
> To upgarde just open a terminal window

sudo apt-get upgrade
sudo apt-get update

err... try it in the reverse order as you want to update your package list before installing updated packages.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Chowderpilot on 2007-04-19
Thanks guys, I gave that a shot and it looks like I"m already good to go. Much appreciated.

---

