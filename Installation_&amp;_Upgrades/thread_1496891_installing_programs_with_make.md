---
title: "installing programs with make"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by cats4gold on 2010-05-29
I've un-tarballed or whatever a program, only to find in needs to be ./configured, made, and make installed, which I have trouble with. Thankfully, the makefile is already made, so no need to ./configure, but I still have trouble. Could someone help?


If you want, pm me and you can do it for me over remote desktop.

---

### Post by bildr on 2010-05-29
what software

and yes you should ./configure before you make even if it has a makefile

the configure script checks for installed libraries on your computer to see if they match what the application needs.  if configure is failing you need some more or different libraries or compilation tools.

why do you need to install from source? did you try a .deb or whatever and it didn't work?

---

### Post by cats4gold on 2010-05-29
> **bildr said:**
> what software

and yes you should ./configure before you make even if it has a makefile

the configure script checks for installed libraries on your computer to see if they match what the application needs.  if configure is failing you need some more or different libraries or compilation tools.

why do you need to install from source? did you try a .deb or whatever and it didn't work?
autotalent, no .deb

I can't ./configure because the folder has only makefile, no configure.

---

### Post by oldos2er on 2010-05-29
There's a PPA for autotalent: [https://launchpad.net/~jeremybubs/+archive/salwenj/](https://launchpad.net/~jeremybubs/+archive/salwenj/)

---

### Post by bildr on 2010-05-29
> **oldos2er said:**
> There's a PPA for autotalent: [https://launchpad.net/~jeremybubs/+archive/salwenj/]("https://launchpad.net/%7Ejeremybubs/+archive/salwenj/")


good catch

---

