---
title: "Problem installing Amarok"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by charlescarroll1 on 2008-02-02
When I attempt to install Amarok using the Add/Remove Applications, I get the following error message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Anybody else get this message?

---

### Post by kellemes on 2008-02-02
> **charlescarroll1 said:**
> When I attempt to install Amarok using the Add/Remove Applications, I get the following error message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Anybody else get this message?


Open the terminal and type..
```
sudo dpkg --configure -a
```

---

### Post by charlescarroll1 on 2008-02-02
I just got another error message using Synaptic Package manager.  Whenever I open Synaptic I get an error message right away.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by charlescarroll1 on 2008-02-02
Ha

Maybe I should have actually read the error message.  I think I rely on you guys too much.

---

