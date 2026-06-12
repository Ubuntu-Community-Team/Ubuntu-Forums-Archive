---
title: "root password"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by szaboar on 2009-12-14
I have installed Ubuntu to my PC. During the install, it didn't ask me for root password.
I can't make a directory outside my home. How can I know the root passwd?
Could anyone help me?

---

### Post by aysiu on 2009-12-14
The root password isn't needed.

If you want to modify a system directory, create a launcher or keyboard shortcut for the command ```
gksudo nautilus
```

If you don't want to bother creating a launcher or keyboard shortcut, you can just press Alt-F2 and paste in ```
gksudo nautilus
``` More details here: [Forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by benjaminsuman on 2009-12-14
Ubuntu doesn't set a root password by default.  Use sudo or gksudo to elevate your permissions.

---

### Post by szaboar on 2009-12-14
Thanks. It works.

---

