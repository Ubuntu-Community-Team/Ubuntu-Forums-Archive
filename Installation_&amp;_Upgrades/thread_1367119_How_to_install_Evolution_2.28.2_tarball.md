---
title: "How to install Evolution 2.28.2 tarball"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by coober85 on 2009-12-29
hey I'm trying to upgrade from 2.28.1 to 2.28.2. 

I've extracted all the tarball files to my desktop (these are separate folders):

evolution-2.28.2 
evolution-exchange-2.28.2  
gtkhtml-3.28.2
evolution-data-server-2.28.2  
evolution-mapi-0.28.2

and I've tried to run the ./configure command in the first one but I get an error saying it doesn't have the correct tools to configure properly. some of these I can find (bison for example) but there are many that don't seem to be available in synaptic. 

Do I need additional repositories or something? if so where do I get these?

What order do I install all of this stuff in? or does it not matter?

Linux Mint 8 (ubuntu 9.10 Karmic Koala)

Thanks

---

### Post by sisco311 on 2009-12-29
Try:
```
sudo apt-get build-dep evolution
```
It should install the needed dependencies.

---

### Post by gradinaruvasile on 2009-12-29
> **coober85 said:**
> hey I'm trying to upgrade from 2.28.1 to 2.28.2. 

I've extracted all the tarball files to my desktop (these are separate folders):

evolution-2.28.2 
evolution-exchange-2.28.2  
gtkhtml-3.28.2
evolution-data-server-2.28.2  
evolution-mapi-0.28.2

and I've tried to run the ./configure command in the first one but I get an error saying it doesn't have the correct tools to configure properly. some of these I can find (bison for example) but there are many that don't seem to be available in synaptic. 

Do I need additional repositories or something? if so where do I get these?

What order do I install all of this stuff in? or does it not matter?

Linux Mint 8 (ubuntu 9.10 Karmic Koala)

Thanks

If you dont know how to install them, i suggest you do not do it. Installing from source will replace files that are in the installed packages and you might create install/uninstall/dependency problems in the future. 
That can be really bad because evolution is a core gnome application with tons of dependencies. So, wait for the official release.

---

