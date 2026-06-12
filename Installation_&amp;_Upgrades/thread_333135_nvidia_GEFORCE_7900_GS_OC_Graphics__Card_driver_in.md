---
title: "nvidia GEFORCE 7900 GS OC Graphics  Card driver instalation"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by shickidyshade on 2007-01-07
Hey guys

Im trying to figure out how and if i can install drivers for nvidia GEFORCE 7900 GS OC Graphics  Card driver instalation that i installed in my new system. I downloaded what i thought was the right 
file off the website but I'm not sure the file is NVIDIA-Linux-x86_64-1.0-9746-pkg2.run

Thanks

---

### Post by taurus on 2007-01-07
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by shickidyshade on 2007-01-07
That worked great is there a 1680 by 1050 resolution possible on edgy

---

### Post by taurus on 2007-01-07
Yes, it is.  Just add "1680x1050" to the front of those resolutions in /etc/X11/xorg.conf (near the end of the file).

```
gksudo gedit /etc/X11/xorg.conf
```

p.s.  I assume you must have a 20.1" LCD widescreen (at least) to go that resolution.  ;)

---

