---
title: "dpkg --configure -a"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by ghindo on 2006-11-15
I recently installed Ubuntu 6.1, and am having difficulties installing any new software.

Whenever I attempt an update or installation, I am told to run```
dpkg --configure -a
```

However, when I open the terminal and attempt to do this, I am told:```
dpkg: requested operation requires superuser privelige
```

I am the only use on this computer, so I'm unsure as to what to do.  Suggestions?

---

### Post by sam81 on 2006-11-16
For getting superuser privileges use:

sudo dpkg --configure -a

you'll then be requested to enter the password. I don't know why you get this message however, you might have some packages left midway in the installation process, and that's stopping you from installing other packages. The dpkg --configure -a should solve the problem. Good luck!

---

