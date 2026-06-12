---
title: "preseed values for PXE install"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by supik007 on 2007-09-10
Hi everyone !! 
For first, please excuse my english...

I build install server for feisty, it works almost good, but there is here few questions i can't answer.

I can install czech language but i cannot configure initrd via pxelinux.cfg/default 
correctly. Adding  
```
append .... auto=true locale=cs_CZ.UTF-8 
```
is correct, but other parameters ... there is not problem with parameters, but I known't possible values ... 
when I append 
```
console-setup/layoutcode=cs, 
```
installer ask me for keyboard layout switching combination, and when after one ask me for hostname, only numeric keyboard works.

So, my question for you is : where I obtain possible values for boot parameters ??  (for feisty at least)

Thaks for every help

Milan

---

