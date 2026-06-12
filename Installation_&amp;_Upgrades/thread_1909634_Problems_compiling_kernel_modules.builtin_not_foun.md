---
title: "Problems compiling kernel: modules.builtin not found."
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by mempman on 2012-01-15
When trying to recompile the kernel, when I try to install modules, I get the following error:


nano@nano-laptop:/usr/src/linux$ sudo make modules_install install
[sudo] password for nano: 
cp: cannot stat `/usr/src/linux-source-2.6.32/modules.builtin': No such file or directory
make: *** [_modinst_] Error 1


There is no file in the directory named modules.builtin.

Any suggestions would be appreciated.  
Thanks.

---

### Post by mempman on 2012-02-03
What i did was create a text file with that name in the corresponding directory and so far the compilation process was able to move forward.

---

