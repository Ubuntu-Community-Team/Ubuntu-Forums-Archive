---
title: "Install options for Server GUI?"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by paulca on 2007-12-24
Linux/Ubuntu folks,

I am having problems setting up a nice visual environment for a Server install? Not sure of the steps involved, or in what order. By the way, I have gotten GNOME working but the terminal windows are all anchored to the upper left (cannot detach or move them) and I cannot resize them. Is this normal behavior for GNOME?

My install steps are:
1. install server
2. apt-get install x-window-system
3. apt-get install gnome

Thanks in advance
Paul

---

### Post by taurus on 2007-12-24
It would be better if you install the ubuntu-desktop package.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by paulca on 2007-12-24
Taurus,

Thank you.

---

