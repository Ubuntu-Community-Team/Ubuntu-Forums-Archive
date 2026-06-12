---
title: "How do I get Desktop Cube to work in 12.04"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2012-09-15
Hello,

How do I get Desktop Cube to work in 12.04?

I have Desktop Cube and Rotate cube selected.  Sometimes it rotates but I only get two desktops, I need 4.

Thanks Hannibal

---

### Post by arsenic23 on 2012-09-15
Install compizconfig-settings-manager [ccsm], open it, go to General Options, select the desktop size tab, set your workspaces up however you like.

---

### Post by coljohnhannibalsmith on 2012-09-15
Thanks arsenic23,

As soon as I do that and click on another desktop both the top and bottom panels dissapear.

This really looks depressing, should I upgrade to 12.10 or can I fix this somehow?

Thanks Hannibal

---

### Post by arsenic23 on 2012-09-16
> **coljohnhannibalsmith said:**
> both the top and bottom panels dissapear.

Wait, what desktop environment are you using?
Also for the traditional 4 workspaces your settings should be this (just to make sure we are on the same page):```
Horizontal Virtual Size: **4**
Vertical Virtual Size: **1**
Number of Desktops: **1**
```

---

### Post by orange2k on 2012-09-16
Look here - a nice and complete guide...

[http://ubuntuforums.org/showthread.php?t=1892851](http://ubuntuforums.org/showthread.php?t=1892851)

---

### Post by coljohnhannibalsmith on 2012-09-16
Thanks guys I think it's working now.

arsenic23, I was confused by the number of desktops and entered 4 instead ofspelling 1.  When I entered 1 as you instructed it stared working again and I didn't lose the panels. BTW, I'm in GNOME3.

orange2k thanks for the manual, I'll definitely bookmark it.

Hannibal

---

