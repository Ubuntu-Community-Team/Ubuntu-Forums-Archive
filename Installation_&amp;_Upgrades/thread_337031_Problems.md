---
title: "Problems"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by tommytwo on 2007-01-12
The power went off during a update, when I went back to updates the waiting update icon was 
gone.  When I attempted to manually update the following message appeared: E: dpkg
was interrupted, you must mannualy run 'dpkg --configure -a' to correct the problen. 

How do I do this?](*,)

---

### Post by MontanaMax on 2007-01-12
open the gnome terminal program (or any other terminal program like x-term or konsole ) and type in the following code

```
sudo dpkg --configure -a
```

---

### Post by tommytwo on 2007-01-13
Thanks MontanaMax>:)

---

