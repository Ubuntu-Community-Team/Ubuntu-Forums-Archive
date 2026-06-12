---
title: "Upgrade to Server Edition"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by bbharatsony on 2008-02-19
How do you upgrade from Ubuntu 7.10 to Ubuntu Server Edition 7.10?

---

### Post by Perpetual on 2008-02-20
Ubuntu Server is basically the same as the desktop version minus the desktop apps and window manager.  Essentially, you would remove all of the apps that you would not use/need on a server then install what you want on the server (mysql, apache, etcetera).

So, you would not be 'upgrading' but basically stripping away all of the desktop gui's.  Honestly, I would think a clean install would be better and reduce the likelihood of problems.

---

### Post by louieb on 2008-02-20
The basic difference is the kernel. You can install the server kernel. 
In Synaptic do a search on **linux-image **to see the kernels available for you.

---

