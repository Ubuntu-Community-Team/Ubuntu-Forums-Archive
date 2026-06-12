---
title: "Installing Kernel Source and Devel"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by D_Murdock on 2007-06-14
I've been trying to compile C code but I don't even have stdio.h. I was told to run "sudo apt-get install kernel-source" and "sudo apt-get install kernel-devel" to obtain the missing libraries, But these aren't working and I'm having no other luck elsewhere. Any suggestions? I'm Running 7.04 Feisty and I'm running the 2.6.20-generic kernel.

any help is appreciated, thanks!

---

### Post by Jussi Kukkonen on 2007-06-14
install the *build-essential* package. That should give you (among other things) all the basic libc header files like stdio.h.

---

