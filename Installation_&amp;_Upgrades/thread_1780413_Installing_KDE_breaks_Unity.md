---
title: "Installing KDE breaks Unity?"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by nitric on 2011-06-12
Hey guys,

Was messing around today and installed kde-standard over my Ubuntu 11.04 install and I played around for a bit but wanted to go back to Unity but I switched it back to Ubuntu at the login and all the menu's are gone, just get my desktop, can right click and was able to make a launcher so I could get online :P but nothing else. any Ideas how to fix this?

-Bill

---

### Post by nitric on 2011-06-12
Ubuntu Classic works fine, also when I installed KDE I switched to kdm instead of gdm maybe that's messed something up?

---

### Post by nitric on 2011-06-12
yeah that seems to be it, running

```
sudo dpkg-reconfigure gdm
```

and switching back to gdm fixed unity.

---

### Post by sikander3786 on 2011-06-12
Strange. Thanks for sharing, I might want to test it as well.

I guess you installed the 'kubuntu-desktop' package however you could've got KDE by just installing the 'kde' meta package.

---

