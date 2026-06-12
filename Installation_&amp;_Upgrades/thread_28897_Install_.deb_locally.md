---
title: "Install .deb locally"
date: 2005-04-22
forum: Installation &amp; Upgrades
---

### Post by defkewl on 2005-04-22
How do I install a .deb file from local computer?

I tried using apt-get install /home/user/deb/filename.deb

and it didn't work

Anybody could give me a clue on this?

---

### Post by Leif on 2005-04-22
dpkg i /home/user/deb/filename.deb

---

### Post by mostwanted on 2005-04-22
use

$ sudo dpkg -i myLocalDeb.deb

---

