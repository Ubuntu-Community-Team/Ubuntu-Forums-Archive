---
title: "Kernel compiling error"
date: 2005-05-27
forum: Installation &amp; Upgrades
---

### Post by mtron on 2005-05-27
I followed the KernelCompileHOWTO from the [wiki](http://www.ubuntulinux.org/wiki/KernelHowto) , but ran into the following problem: 

when i wanna run "make gconfig" i get the error

HOSTCC  scripts/basic/fixdep
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o: file not recognized: 
File for mat not recognized
collect2: ld returned 1 exit status
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2
michael@box:/usr/src/linux-source-2.6.10$

i don't know what this means, google also could not help me. especially the /../../../ is very strage.

Can someone help me please?

---

### Post by alastair on 2005-05-27
Don't know. But what does "make xconfig" do?

---

### Post by mtron on 2005-05-28
the same...

Strange. well, i have also debian , and compiled my custom kernel for ubuntu there.

---

