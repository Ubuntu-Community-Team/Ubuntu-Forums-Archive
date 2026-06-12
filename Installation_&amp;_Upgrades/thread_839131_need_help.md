---
title: "need help"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by johnAU on 2008-06-24
I have installed ubuntu a few days ago but now i can't download updates. I keep on getting the following.
E:/var/cache/apt/archives/utl-linux_2.13.1-5 uruntu_i386 deb
subprocess new pre-removal script returned error exit status 139

---

### Post by erginemr on 2008-06-24
Hello,

Try to flush your package cache form the terminal first with:
```
sudo aptitude clean
```
If this doesn't work, then try the following commands in an effort to fix the package management system:
```
sudo dpkg --configure -a
sudo apt-get install -f
```

And please use a more descriptive title to your topic instead of the generic "need help" one.

---

