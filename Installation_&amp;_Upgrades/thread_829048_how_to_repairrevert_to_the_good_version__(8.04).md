---
title: "how to repair/revert to the good version ? (8.04)"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by Andre-D on 2008-06-14
I switched on extra updates, not only the "approved" updates.
now I have problems with samba.
how can I "reinstall"/"revert" to original Ubuntu 8.04 - reverting back to approved updates only?

---

### Post by hoboken on 2008-06-14
system - administration - synaptic package manager, then click package, repositories, updates. From there you can manage your updates. 

However, if you're having problems with samba it means the update was already installed. Not sure how easy it is to roll back a program..

---

### Post by Andre-D on 2008-06-14
That's why I am trying to find out, I am also ruing kernel ...19 , I could start by booting an older one :) - not sure how good solution that is, and what is the latest official kernel.

---

### Post by avtolle on 2008-06-14
.19 is, AFAIK, the latest "official" kernel, as this kernel has been available to all my computers, some of which are set up to the "approved" repos only.

For Samba; before changing your software sources list, mark the installed version for total removal under Synaptic; hit apply. Then, update your sources list as suggested above, reload, open Synaptic and install Samba from there. HTH.

---

### Post by housam on 2008-06-14
Maybe booting from older kernel could solve the problem.

---

