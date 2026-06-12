---
title: "Removing source application?"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by xsystemx on 2008-03-14
I recently installed webmin using the source code provided off their website, I was wondering how I could remove this application ?

For example, binaries are simple, sudo apt-get remove name

But how to I uninstall something that was compiled using source code?

---

### Post by taurus on 2008-03-14
In the same directory that you built it, just use the uninstall to remove it.

```
sudo make uninstall
```

---

### Post by xsystemx on 2008-03-14
What if the source directory has already been deleted?

---

### Post by jose158 on 2008-03-14
Same here. I wanted to remove Wallpapoz, but I already deleted the source directory...

---

### Post by zvacet on 2008-03-15
```
sudo dpkg --remove --force-remove-reinstreq** package_name**
```

---

