---
title: "what is the package name for libc? (ubuntu)"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by franpa on 2006-10-14
i need this and am unsure about what else is needed to complete my installing of video drivers... i have figured out so far...

a) how to exit the xterminal
b) the apt-get command (apt-get install package)
c) sudo is the root user
d) gnome is the gui

---

### Post by franpa on 2006-10-14
don't worry...

apt-get install libc-dev

---

### Post by franpa on 2006-10-15
lock me :)

---

### Post by K.Mandla on 2006-10-16
:D Glad to see you found it.

If you wanted to (and perhaps you knew this), you could search [http://packages.ubuntu.com](http://packages.ubuntu.com) for libc, or use 

```
sudo apt-cache search _______
```
to find a package. The Web-based version is generally more usable, though. :) Cheers!

---

### Post by franpa on 2006-10-16
apt-cache? is that diff to "aptitude search"?

---

### Post by K.Mandla on 2006-10-16
It's similar. *aptitude search* seems to give more information, while *apt-cache search* just spits out package names. I'm sure there are other differences too. The man pages would probably explain them better.

---

