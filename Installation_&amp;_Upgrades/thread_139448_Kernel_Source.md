---
title: "Kernel Source"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by twebster80 on 2006-03-04
I need to install the kernel source so i can compile my winmodem driver. I cannot get on the internet without it so I need to know how to determine which kernel I am using and what individual .deb files i need to download. I am going to download them in Win XP and copy over to Ubuntu. Any help is appreciated

---

### Post by az on 2006-03-04
[QUOTE=twebster80]I need to install the kernel source so i can compile my winmodem driver. I cannot get on the internet without it so I need to know how to determine which kernel I am using and what individual .deb files i need to download. I am going to download them in Win XP and copy over to Ubuntu. Any help is appreciated[/QUOTE]
You don't need the full source, just the headers.  The apropriate linux-headers package is on the install cd.

You do need a different version of gcc than is on the cd, though - that was an oversight.  You need the gcc-3.4, gcc-3.4-common and cpp3.4 packages.  

Download them from 
packages.ubuntu.com
and transfer them to your ubuntu box.  

sudo dpkg -i *.deb

---

### Post by twebster80 on 2006-03-04
Thank you for the help...So gcc 4.0 is bad on the cd?

---

### Post by akiro.yamamoto on 2006-03-04
It's not corupted it's just that some apps require gcc 3.4.

---

### Post by twebster80 on 2006-03-04
oh ok thanks for the help...hopefully my next post will be from Ubuntu and not on XP...Talk to you guys later

---

