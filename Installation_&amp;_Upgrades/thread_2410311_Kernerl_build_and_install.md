---
title: "Kernerl build and install"
date: 2019-01-14
forum: Installation &amp; Upgrades
---

### Post by sylvain30 on 2019-01-14
Dear all,

 Previoulsy I used the ```
make-kpkg 
``` to package kernel newly built. On the command line I can add the option ```
--apped-to-version=xxxxxx 
```in order to modify (specialize) the name of the package and of the Kernel.
 But now I follow another tutorial to build the kernel and on the command line I can't set something to differentiate the outputs. The new command line is 
 ```
fakeroot debian/rules binary
```

Could you help me to find the simplest and most efficient way to produce a kernel (and package) with a dedicated suffix ?

 I've looked for "make-kpkg" in scripts in my build folder without success. So this command is not used now. 
the new tutorial I'm trying to use is [https://ahelpme.com/linux/ubuntu/rebuild-the-official-ubuntu-kernel-ubuntu-16-04-lts/](https://ahelpme.com/linux/ubuntu/rebuild-the-official-ubuntu-kernel-ubuntu-16-04-lts/)

I need your help.

 Thank a lot.

---

