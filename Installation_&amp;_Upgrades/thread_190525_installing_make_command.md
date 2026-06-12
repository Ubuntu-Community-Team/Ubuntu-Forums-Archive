---
title: "installing make command"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by pradeep79 on 2006-06-06
I tried installing a new package and the make command is not found in the system. Can someone tell me which package I have to install if I want to get the make command.

---

### Post by madscientist on 2006-06-06
You want to install the "make" package (surprise!! :-D )

Alternatively, you could install the build-essentials package to get all the stuff you need to compile on your system (make plus compilers, etc.)

---

### Post by pradeep79 on 2006-06-06
Thanks a lot madscientist, its quite surprising that you gotta install it, I thought its a built-in package to install other packages.

---

### Post by rcarring on 2006-06-06
Run synaptic (Gnome desktop) or Adept (KDE desktop)

Synaptic:

Click on all
Mark for installation --

gcc
make

Click apply

The compiler, binutils and make will be installed on your system.

Not sure what equivalent is under adept as i don't run Kubuntu

---

### Post by madscientist on 2006-06-06
[QUOTE=pradeep79]Thanks a lot madscientist, its quite surprising that you gotta install it, I thought its a built-in package to install other packages.[/QUOTE]A standard Ubuntu system is configured as a desktop user box, not a developer's workstation.  So, it doesn't come with any compilers, build tools (like make), etc. installed.  The "build-essential" package will get you everything you need to start building C and C++ code on your desktop.

Have fun!

---

### Post by rcarring on 2006-06-06
Go with madscientist's suggestion if you need the additional build tools.

---

### Post by judesoul on 2006-06-06
hi,

would like to ask on were can i found this build-essentials packages? i also have no make command...please help...i'm a noob with....!

thank you

---

### Post by rcarring on 2006-06-06
You don't need to the build-essentials if all you want to do is compile and make in C.

Install gcc and make from synaptic package manager.

---

