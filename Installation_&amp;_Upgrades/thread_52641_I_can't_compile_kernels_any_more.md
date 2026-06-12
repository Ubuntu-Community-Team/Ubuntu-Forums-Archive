---
title: "I can't compile kernels any more"
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by tseliot on 2005-07-28
Hi, today I've compiled a (vanilla) kernel and everything went ok. I rebooted with the new kernel and now I can't compile. I stepped back to my previuos kernel and I got the same error:

alberto@ubuntu:/usr/src/linux$ sudo make menuconfig
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc-3.4: command not found
make[1]: *** [scripts/basic/fixdep] Error 127
make: *** [scripts_basic] Error 2


P.S. I'm trying to compile a Breezy kernel (from Hoary). I had tried it before and it worked before

---

### Post by tseliot on 2005-07-28
I reinstalled Ubuntu yesterday night. I've made only 1 compilation with this installation. This is weird.

---

### Post by geearf on 2005-07-28
you do not have gcc 3.4 that's all.

---

### Post by tseliot on 2005-07-28
Only gcc 3.4 base was installed. But how did I compile that kernel before???

Thanks, now it works.

---

### Post by DonVla on 2005-07-28
why haven't you tried 

> apt-get --reinstall install gcc-3.4 (gcc 3.3) 

it's easier than reinstalling ubuntu.

---

