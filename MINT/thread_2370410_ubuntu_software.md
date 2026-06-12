---
title: "ubuntu software"
date: 2017-09-02
forum: MINT
---

### Post by openation1 on 2017-09-02
Hello everyone, I have an issue with ubuntu software. I can't open it. I tried  ( sudo purge ubuntu-software) and then reinstalling it again ( sudo install ubuntu-software) and now it doesn't come out at all. I can't even find it . Please Help me thank you

---

### Post by ajgreeny on 2017-09-03
More detail needed please.
Which version of Ubuntu?
What DE are you using; unity, gnome-shell, xfce4, lxde?

Is your system fully updated using **sudo apt-get update; sudo apt-get upgrade**?

---

### Post by vasa1 on 2017-09-03
> **openation1 said:**
> Hello everyone, I have an issue with ubuntu software. I can't open it. I tried  ( sudo purge ubuntu-software) and then reinstalling it again ( sudo install ubuntu-software) and now it doesn't come out at all. I can't even find it . Please Help me thank you
Your commands should be
```
sudo apt-get purge ubuntu-software
```and```
sudo apt-get install ubuntu-software
```Note the "apt-get".

---

