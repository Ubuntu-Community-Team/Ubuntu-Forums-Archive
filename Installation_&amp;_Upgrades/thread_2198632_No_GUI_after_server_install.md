---
title: "No GUI after server install"
date: 2014-01-09
forum: Installation &amp; Upgrades
---

### Post by VA3WPN on 2014-01-09
After I do the install of the latest Ubuntu Server.... I get no GUI. I am able to Get the Cmd Promt and login that way, but there is a TON of things I need to do that use the GUI. 

Any suggestions as to what I should be looking for? Thanks?

---

### Post by mörgæs on 2014-01-09
A server ISO does not contain a GUI.

The command

```
sudo apt-get install lxde
```

(for example) adds a minimal GUI to a server install.

---

