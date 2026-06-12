---
title: "&quot;unable to resolve host ubuntu&quot;"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by ray field on 2010-01-02
I'm trying to use a flash drive to try to repair the Intrepid installation on my netbook.  

when I drop to a terminal and try "sudo apt-get update" i get

```
sudo: unable to resolve host ubuntu
E: The method driver /usr/lib/apt/methods/https could not be found
E: The method driver /usr/lib/apt/methods/https could not be found
```

ideas?

---

### Post by sgosnell on 2010-01-02
Sounds like a bad line in your /etc/apt/sources.list file.  Edit that as root and see if there isn't a badly formed line somewhere.

---

