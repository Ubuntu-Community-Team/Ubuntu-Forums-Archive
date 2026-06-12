---
title: "Xubuntu: creating a minimal install"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by Abecedaria on 2006-12-14
Hello,

I'm trying to create as minimal an install as possible to save disk space on an old laptop. I don't need things like Gaim, Gnumeric, Gimp, dvd burning tools, etc. However, when i try to remove them with synaptic, it requires that I remove the ubuntu-desktop package, which I assume I don't want to do!

Any suggestion for removing these individual packages?

Thanks,
abc

---

### Post by K.Mandla on 2006-12-14
Start with a server install, and add

```
sudo aptitude install x-window-system-core xfce4
```
I should add one caveat: I've had trouble getting that going with Edgy, but I know for a fact it's 100 percent working in Dapper. Edgy changes the packages somehow and the start command *startxfce4* doesn't seem to work. 

By the way, you can remove ubuntu-desktop. It's just a metapackage to hold everything else in place -- kind of like a bottlecap. Removing it doesn't necessarily remove everything it holds in place. ;)

Edit: You might also look into *debfoster*, which walks through each package installed on your machine, and asks if you want to pull it and its dependencies. Very powerful, but very dangerous too. Make sure you know what you're doing with that stuff. :D

---

