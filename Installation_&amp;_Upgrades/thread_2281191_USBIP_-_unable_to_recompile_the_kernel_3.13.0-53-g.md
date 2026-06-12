---
title: "USBIP - unable to recompile the kernel 3.13.0-53-generic"
date: 2015-06-05
forum: Installation &amp; Upgrades
---

### Post by andrej7 on 2015-06-05
Hello, I can't get usbip module to work,

First I tried compiling directly from tar.gz source and FAILED.
Now I'm trying with these commands:

aptitude update
aptitude install usbip usbip-source module-assistant
m-a prepare
[I]Getting source for kernel version: 3.13.0-53-generic
apt-get install linux-headers-3.13.0-53-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-3.13.0-53-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.

[/I]m-a update
apt-get install linux-headers-3.13.0-53-generic AGAIN just in case :)
m-a a-i usbip-source FAILED - looks like it cant find kernel source files? It suggests running apt-get install linux-headers-3.13.0-53-generic and exits.

When doing make menuconfig I've noticed that USB/IP modules are already selected by default...

[I]modprobe usbip
FATAL: Module usbip not found.


[/I]

---

### Post by dino99 on 2015-06-05
you need the 'sources' archive activated (deb-src)

---

### Post by andrej7 on 2015-06-05
I already have all deb-src sources uncommented in  /etc/apt/sources.list 
Can you write some step-by-step how-to, I haven't recompiled the kernel since 2007 (make menuconfig & make bzImage & make install were only commands needed back then) :p
Or even better: try to get usbip module working on your system ;)

---

