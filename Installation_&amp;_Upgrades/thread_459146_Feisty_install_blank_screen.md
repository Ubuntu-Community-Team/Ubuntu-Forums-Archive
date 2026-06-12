---
title: "Feisty install blank screen"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by bbejeck on 2007-05-30
Hi,

I tried to install Feisty from a iso burned to cd.  My laptop boots from CD fine but when it is finished I just have a blank screen with a brown background.  If I try to start in graphics safe mode, I get an X is not configured error.  What should I do next?

---

### Post by loathsome on 2007-05-30
Did you do anything when done installing? It looks like you've (or the installation process) messed up the xorg.conf file.

You could try to generate a new one using this command ```
sudo dpkg-reconfigure xserver-xorg
```

(Get to a console by pressing CTRL+ALT+F1)

Good luck.

---

### Post by bbejeck on 2007-05-30
Hi,

I tried that with a the -phigh parameter and nothing happpened.  I will try again with no parameter.

---

