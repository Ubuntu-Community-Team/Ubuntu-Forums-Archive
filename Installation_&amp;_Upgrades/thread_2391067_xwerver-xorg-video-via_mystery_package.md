---
title: "xwerver-xorg-video-via mystery package"
date: 2018-05-05
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2018-05-05
I have a package listed named xwerver-xorg-video-via the description that it is a transitional package to new drivers.

I recently had some problems with the dpkg status file and package lists due to some faulty memory which was mucking things up. I have replaced the memory and now am getting some apparently harmless errors related to a package called xwerver-xorg-video-via, which doesn't seem to be a real package. 

I have found reverences to a package called xserver-xorg-via, which is not in the current synaptic package lists for installation. It appears it was superseded on 2010-03-22 by i386 build of xserver-xorg-video-openchrome 

I think I can remove the package without any problems but does anyone know for sure?

---

### Post by deadflowr on 2018-05-05
xwerver?
if you run apt purge with the simulate option what happens?
(I'm guessing:
```
sudo apt purge -s xwerver-xorg-video-via
```

Still, xwerver?
huh. weird.

---

### Post by rsteinmetz70112 on 2018-05-06
As I posted I was having some weird problems due to memory. I think it was randomly corrupting the dpkg files. Synaptic showed the package as installed. I deleted it in Synaptic and everything seems to be fine now. But I can't run the test you suggested. I do wonder if everything else is ok.

---

### Post by deadflowr on 2018-05-06
Well double check that the actual xserver packages are still installed.
either in synaptic or
```
dpkg -l | grep xserver
```
should output a decent list.

---

