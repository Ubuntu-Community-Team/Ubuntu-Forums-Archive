---
title: "[SOLVED] trouble upgrading to 7.10"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by perroflaco on 2008-09-16
I tried upgrading from 7.4 to 7.10 using Update Manager and I get the following error message

Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://blognux.free.fr/debian/dists/unstable/main/binary-i386/Packages.gz](http://blognux.free.fr/debian/dists/unstable/main/binary-i386/Packages.gz) 404 Not Found

Any help would be greatly appreciated.

---

### Post by Partyboi2 on 2008-09-17
Before trying to upgrade to gusty open up your Software Sources (System>Admin>Software Sources) and disable all 3rd party repos

---

### Post by Sef on 2008-09-17
> I tried upgrading from 7.4 to 7.10 using Update Manager and I get the following error message

Failed to fetch [http://www.getautomatix.com/apt/dist...86/Packages.gz]("http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz") 404 Not Found
Failed to fetch [http://blognux.free.fr/debian/dists/...86/Packages.gz]("http://blognux.free.fr/debian/dists/unstable/main/binary-i386/Packages.gz") 404 Not Found

Any help would be greatly appreciated.

First, have you **back up **your files?

Second, Application > Accessories > Terminal

then paste or type in this code:

```
gksudo gedit /etc/apt/sources.list
```

Next, comment out those two lines.  To comment out a line, put a # before it.

They should look like this in the sources list.

>  #[http://www.getautomatix.com/apt/dist...86/Packages.gz]("http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz") 
 #[http://blognux.free.fr/debian/dists/...86/Packages.gz]("http://blognux.free.fr/debian/dists/unstable/main/binary-i386/Packages.gz") 

Last, try updating again.

---

### Post by perroflaco on 2008-09-17
I tried your suggestion and it seems to be working. Now I'm just waiting for all the fetching to be done.

---

### Post by perroflaco on 2008-09-17
7.10 now running. Thanks for all the help.

---

