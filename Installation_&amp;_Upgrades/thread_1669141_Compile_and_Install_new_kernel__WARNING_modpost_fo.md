---
title: "Compile and Install new kernel : WARNING: modpost: found X section mismatch(es) ?!?"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by yperionas on 2011-01-17
Hello everybody, thank you for reading this post hoping that you bring along some very helpful ideas.

I am trying to compile and install a new kernel. I have downloaded the  2.6.37 version from kernel.org and I have extracted it in  usr/src/linux-2.6.37/ folder.

I have tried to compile it and install it according to the instruction  given in the following web site and which I found very useful: [http://www.digitalhermit.com/linux/K...WTO.html#INTRO]("http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html#INTRO")

Nevertheless, I am encountering some problems during the make install  modules process as I get some warnings (i.e. The title of this post).

I thought to ignore the warnings and continue by copying the modules in  /lib/modules/linux-2.6.37 but this is not possible since at that  directory there is no folder created with the new kernel I am trying to  install and thus I get a msg saying: **FATAL: could not load /lib/modules/2.6.37/modules.dep**.

The warning message: **WARNING: modpost: found X section mismatch(es)** suggests to run a **make CONFIG_DEBUG_SECTION_MISMATCH=y**.
At the moment I am running a make again and saving the output to a file  so that I can see later on what are the mismatches that I get. In any  case we are talking about more than 50 mismatches so I am wondering if  these mismatches are not that serious and the problem I cannot install  and copy the modules is something else that I am missing as I am new to  Linux.

---

### Post by dino99 on 2011-01-17
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

