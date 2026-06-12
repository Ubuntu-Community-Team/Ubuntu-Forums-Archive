---
title: "how to get error listing after fresh install"
date: 2005-10-05
forum: Installation &amp; Upgrades
---

### Post by sd_ap on 2005-10-05
after the first reboot, when apps start to install, I always get an error or three...which log file can I look at to see what went wrong/happened so I can post it up and see if anyone else had my problems? :)


example:
```

unpacking gnome-menus (from .../gnome-menus_2.10-0ubuntu1_i386.deb) ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status2
free():invaluid pointer 0xb7fe3038!

```

cheers!
-sean

---

### Post by sd_ap on 2005-10-05
update:

the gnome issues have caused dep issues throughout the rest of my install...its spitting errors out left, center, and right!!

looks like whatever address it was pulling the packages from is having SERIOUS issues cause when I went into aptitude to clean all downloads and re-grab them, i got the same errors with the gnome files...

*sigh*


i found what caused my errors :)  

but still, it would be nice to see an install-error-log if it exists.

---

