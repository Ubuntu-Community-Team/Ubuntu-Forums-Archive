---
title: "Package manager issues"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by phillmathis on 2008-07-27
Hey guys and girls - I have a problem with my package manager -  an error occurs everytime i start it saying that i need to run "dkpg --configure -a"; I try to run this but it gets as far as saying that it is starting depmod and then freezes - I've left it for hours to sort itself out but no luck - any advice??:confused:

---

### Post by Sef on 2008-07-27
Applications > Accessories > Terminal

then copy/paste or type in this code:

```
sudo dkpg --configure -a
```

then ```
sudo apt-get update
```

---

### Post by phillmathis on 2008-07-27
i do that and it starts doing something then just freezes the whole computer??? Any other ideas?:(

I get as far as "dpkg --configure -a" before it freezes up then it just dies.

---

