---
title: "Gparted Instialtion Question"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by MattF on 2007-04-17
Hi ... in trying to install Gparted I've run into an error ..." configure: error: C compiler cannot create executables".   As I'm new to Ubuntu, I'm not sure how to proceed.  Any suggestions would be great :-)

The basic plan is to get enough partitioin space (on a second drive) to install a couple of programs , Matlab and R.

thanks
--MattF

---

### Post by taurus on 2007-04-17
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by MattF on 2007-04-17
thanks :) ... it seems that one step leads to another ... in this case a new error ...
"configure: error: *** uuid library (libuuid) not found"

Any thoughts ??

thanks
--MattF

---

