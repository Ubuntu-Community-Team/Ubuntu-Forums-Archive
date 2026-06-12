---
title: "atmelwlandriver compilation source..."
date: 2004-11-11
forum: Installation &amp; Upgrades
---

### Post by Gehost on 2004-11-11
Hi,

I have a pcmcia card with prism2 chipset (Sitecom wl-011 v2) and the driver for linux is the atmelwlandriver. So, I could download the source from the universe ubuntu server; and now I have to compile that...  :sad:  I tried... 
make realclean
make config
make all   ==> errors!

But In fact, in the readme file it ask for recompiling kernel source if certain options is not enabled...

Somebody had the problem? Someone have already compile these sources?

---

### Post by az on 2004-11-12
You have the intersil radio on an atmel chipset, right?

[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#Atmel](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#Atmel)

Did you install build-essential?  You also need the kernel-headers.

Search for linux-headers and kbuild with synaptic.  Use the kernel-headers directory (look in /usr/src) as your source tree when prompted...

---

### Post by Gehost on 2004-11-12
Ok, I'll retry with that... 

But I've installed linux-kernel-headers (ubuntu version), and there's no file in /usr/src/Linux_X.X.XX.../ like normally...

How can I see where are the source file of kernel? 

 #-o

---

### Post by Gehost on 2004-11-13
So... When I try "make", an error occure cos I don't have the folder /lib/modules/linux-2.6.8.1-3-386/build (here the folder missing is "build")...

Any idea? ](*,)

---

### Post by az on 2004-11-13
The package is linux-headers-2.6-386

There is also a linux-kernel-headers package, but that is something else.

Yes, this is confusing.  Good luck.

---

### Post by Magneto on 2004-11-13
[QUOTE=Gehost]So... When I try "make", an error occure cos I don't have the folder /lib/modules/linux-2.6.8.1-3-386/build (here the folder missing is "build")...

Any idea? ](*,)[/QUOTE]
do this 

sudo ln -s /usr/src/linux /lib/modules/linux-2.6.8.1-3-386/build

or link it to whatever kernel source folder u have in /usr/src

---

