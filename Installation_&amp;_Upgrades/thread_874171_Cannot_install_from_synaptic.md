---
title: "Cannot install from synaptic"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by jakespet on 2008-07-29
I just upgraded to ubuntu 8.04 and now I cannot install any software via synaptic. It seems to download them, but will not install them. Is there something that can be done to fix this problem?
Thanks
Jakespet

---

### Post by gjoellee on 2008-07-29
you may have checked "download only"...we in the forum would be glad if you could give some more info...

---

### Post by Pumalite on 2008-07-29
Post:
cat /etc/apt/sources.list

---

### Post by jakespet on 2008-07-29
I get a code 2 error

---

### Post by Pumalite on 2008-07-29
Post the entire output of:
sudo dpkg --configure -a

---

### Post by jakespet on 2008-07-29
Here is screenshot

---

### Post by Pumalite on 2008-07-29
Two hyphens:
sudo dpkg --configure -a

---

