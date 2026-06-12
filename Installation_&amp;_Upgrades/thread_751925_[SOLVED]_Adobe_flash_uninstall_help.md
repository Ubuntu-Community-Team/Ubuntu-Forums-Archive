---
title: "[SOLVED] Adobe flash uninstall help??"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by dD3v1L on 2008-04-11
Hi, Im quite new to ubuntu. I had problems when installing adobe flash. My internet line went down and the installation progress got jammed. So i forced the window to quit.

Now Im not able to run synaptics.. Whenever I try to, this error message appears:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How do I solve this? Thanks in advance.

---

### Post by Partyboi2 on 2008-04-11
trying opening a terminal (Applications>Accessories>Terminal) and typing
```
sudo dpkg --configure -a
``````
sudo apt-get update
```

---

### Post by dD3v1L on 2008-04-11
Whew.. That worked. Thanks :D

---

### Post by buried on 2008-04-11
Will you re-install it :P
This thread is solved then.

---

