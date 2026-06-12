---
title: "[SOLVED] Filled up /"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by colddayinapril on 2007-12-14
OK, so here's what happened:

I wanted to Install Kubuntu, to try out KDE, see if i Liked it. I installed *kubuntu-desktop* meta package via synaptic. However, I didn't take into account the amount of space this would require, and my / folder filled up before the operation could be completed and it terminated the install. But, instead of deleting the files, it left them there. So now I can't even watch videos online, cause firefox has no room to cash the movies! :/

so, anyone know where synaptic would have put these files, so I can go in and manually delete them?

---

### Post by diatribe on 2007-12-14
use synaptic to remove them, also you want around 10gb for / for future reference, assuming you have a sepearte home directory

---

### Post by taurus on 2007-12-14
Applications -> Accessories -> Terminal
```
sudo apt-get clean
df -h
```

---

### Post by mikewhatever on 2007-12-14
Run <sudo apt-get clean>. It will delete all of the downloaded packages from the cache.

---

### Post by colddayinapril on 2007-12-15
Thanks guys... worked like a charm :)

---

