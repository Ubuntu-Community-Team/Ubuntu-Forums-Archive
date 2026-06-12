---
title: "Synaptic Package Manager Error"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by urbanjugle on 2008-05-10
Synaptic Package Manager Error

When I try to open Synaptic Package Manager it will NOT open and gives me an error;
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I open a terminal and enter dpkg --configure -a , I get the following error;
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

How do I fix this?

---

### Post by Rocket2DMn on 2008-05-10
Surprised nobody answered this.  You need to use sudo for this command
```
sudo dpkg --configure -a
```

---

### Post by talon 2 on 2008-05-11
> **Rocket2DMn said:**
> Surprised nobody answered this.  You need to use sudo for this command
```
sudo dpkg --configure -a
```


Thanks  Rocket2DMn for your post. I had the same problem. I am working with hardy heron and my system crashed as I was installing programs through the package manager. All is good again....

---

