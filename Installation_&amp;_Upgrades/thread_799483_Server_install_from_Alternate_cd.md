---
title: "Server install from Alternate cd"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by cbhargava on 2008-05-19
Hello,

Is it possible to install a cli (server) system using the alternate CD (8.04)?

Thanks.

---

### Post by sgk on 2008-05-19
yes, the only thing is that you do not have live install. you must install it using text based installer

---

### Post by iaculallad on 2008-05-19
Try visiting this [link]("https://help.ubuntu.com/community/Installation/I386") for some information regarding the installation of Ubuntu Alternate CD's. Same process applies with the installation of Hardy.

---

### Post by prshah on 2008-05-19
> **cbhargava said:**
> 
Is it possible to install a cli (server) system using the alternate CD (8.04)?

Eh? The ubuntu-server install already installs only a command line interface. 

Any particular reason why you want to use the "alternate" CD only?

---

### Post by cbhargava on 2008-05-19
Reason is to carry only *one* ubuntu CD in my CD wallet for both desktop and server install.

> **prshah said:**
> Eh? The ubuntu-server install already installs only a command line interface. 

Any particular reason why you want to use the "alternate" CD only?

---

### Post by cbhargava on 2008-05-19
Thanks. I just want to install the base system, is there a way to avoid the installation Xorg and other desktop packages?


> **iaculallad said:**
> Try visiting this [link]("https://help.ubuntu.com/community/Installation/I386") for some information regarding the installation of Ubuntu Alternate CD's. Same process applies with the installation of Hardy.

---

### Post by iaculallad on 2008-05-19
> **cbhargava said:**
> Thanks. I just want to install the base system, is there a way to avoid the installation Xorg and other desktop packages?

If what you're planning to install is a SOHO server (and don't give in too much security), give (X)Ubuntu a try. Since it only has a minimalistic GUI. Or you could just issue the command **aptitude install xubuntu-desktop** on your terminal since all Ubuntu flavors comes in the same family and carries with them the same package.

---

### Post by cbhargava on 2008-07-13
Hitting F4 (at boot menu) on the alternate CD and choosing command line installation was what I wanted. Thanks for answers though.:KS

---

