---
title: "Reinstalling &quot;Default&quot; ubuntu packages"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by bcr821 on 2007-11-16
Recently i got curious about the different flavors of ubuntu and decided to install kubuntu-desktop and xubuntu-desktop on my computer.  After installing them i wanted to uninstall them so using aptitude i removed the packages.  

However in the process of doing this it seems some of the "default" ubuntu packages were removed (for example one of my media players).  I was wondering if there was some aptitude command that would allow me to reinstall all the default packages that came with ubuntu Gutsy

Thanks

---

### Post by forestpixie on 2007-11-16
you could try

```
sudo aptitude install ubuntu-desktop
```

---

### Post by Goldiescorpio on 2007-11-16
Hi there!

you can try to reinstall the default ubuntu desktop by the following command:

Sudo apt-get install ubuntu-desktop

Normally it is about 2GB, but you can easily see that before installing: Apt-get will say sthing like:

x packages already newest version, x packets about to install...

I hope this was of some help.

Grtz

Damn, seems like someone was typing faster ;-)

---

