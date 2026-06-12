---
title: "update error"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by nateandjennie on 2008-11-01
Hey,

I'm completely new to ubuntu and linux for that matter.  I installed 8.04 a while back and never really touched it.  I started it up not too long ago and notice that there were many updates waiting, but when I went to update I got an error message like the one below.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can someone tell me what this means and what I can do about it?

Thanks

---

### Post by taurus on 2008-11-01
Close Update window manager or whatever you have opened first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```
Now, see if you can Update this time.

---

### Post by nateandjennie on 2008-11-02
thanks a ton!  This worked perfectly!

---

