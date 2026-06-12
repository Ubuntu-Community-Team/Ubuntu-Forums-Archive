---
title: "Is there an apt command equivalent to yum localinstall?"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by JimGvo on 2008-08-05
Sometimes I get .deb files that I need to install but end up in dependency hell getting them installed.  Yum solves that problem with the localinstall option, is there a way to do the same thing using any of the apt/dpkg tools?

Thanks,
Jim.

---

### Post by kerry_s on 2008-08-05
```
dpkg -i filename.deb 
```

you can also just click on the deb if gdebi is installed, it usually is.

---

### Post by JimGvo on 2008-08-05
> **kerry_s said:**
> ```
dpkg -i filename.deb 
```

you can also just click on the deb if gdebi is installed, it usually is.

I don't know about gdebi, but dpkg -i is definitely not the same as yum localinstall.  Yum localinstall will attempt to satisfy and load dependencies.  Dpkg does not, unless it's changed recently.

Does gdebi resolve dependencies?

What I'm looking for is an apt-get install xxx.deb but I don't think that works.

Thanks,
Jim.

---

### Post by kerry_s on 2008-08-05
> **JimGvo said:**
> I don't know about gdebi, but dpkg -i is definitely not the same as yum localinstall.  Yum localinstall will attempt to satisfy and load dependencies.  Dpkg does not, unless it's changed recently.

Does gdebi resolve dependencies?

What I'm looking for is an apt-get install xxx.deb but I don't think that works.

Thanks,
Jim.

no dpkg does not, after running "dpkg -i" you run "apt-get -f install" that will grab any missing depends.

yes, gdebi resolves dependency's.

> 
Simple tool to install deb files

gdebi lets you install local deb packages resolving and installing its dependencies. apt does the same, but only for remote (http, ftp) located packages.

This package contains the graphical user interface. 

here's the manual for apt/dpkg, as it's good to know how to use:
[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)

---

### Post by JimGvo on 2008-08-05
OK that's what I'm looking for.  Thanks!

Jim.

---

