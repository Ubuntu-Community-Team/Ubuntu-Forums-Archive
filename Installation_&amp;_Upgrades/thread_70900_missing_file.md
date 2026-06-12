---
title: "missing file?"
date: 2005-10-01
forum: Installation &amp; Upgrades
---

### Post by fiby on 2005-10-01
newbie, but i need /lib/modues/2.6.10-5-386/build to be created, i need to link the kernel source to the modules....  trying to install ndiswrapper.........it wont make, or make install cause it say directory not there and it isn't?  Any ideas
Fiby

---

### Post by mlomker on 2005-10-01
It sounds like you need the kernel headers.

```

sudo apt-get install linux-headers-$(uname -r)

```

---

