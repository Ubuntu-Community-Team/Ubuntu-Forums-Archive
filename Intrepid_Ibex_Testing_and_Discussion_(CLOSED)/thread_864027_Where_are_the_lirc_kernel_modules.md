---
title: "Where are the lirc kernel modules"
date: 2008-07-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rlowery on 2008-07-19
Previously (eg in hardy), lirc kernel modules are found in the linux-ubuntu-modules package.  Intrepid does not appear to contain this package.

Have these modules been moved?, or do I just need to be patient :)

Thanks

-Rob

---

### Post by psyke83 on 2008-07-19
I bet these modules are compiled using DKMS and the "lirc-modules-source" package. I tried installing it but got some build errors for a module, but I don't know if they were fatal. Try it and see.

---

### Post by Timon&amp;Pumba on 2008-07-20
The DKMS is the way to go to get the lirc modules back.
However, building the module does give errors indeed:
```

$ sudo dkms build -m lirc -v 0.8.3

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
pushd /var/lib/dkms/lirc/0.8.3/build; make debconf KSRC=/lib/modules/2.6.26-4-generic/build KVER=2.6.26-4-generic; popd....

Error!  Build of lirc_atiusb.ko failed for: 2.6.26-4-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/lirc/0.8.3/build/ for more information.

```

The file make.log does not give any useful information.
Guess we have to wait for some fixes.

However, DKMS thinks that the module is build, although it failed. I think that is strange, because as a user you may think everything went ok, if you do not pay enough attention.
You have to manually rerun DKMS again.
This issue was the same reason I struggled with the new nvidia driver. Somehow it was not build by DKMS and I thought it had installed nicely.

---

### Post by antiram on 2008-07-24
1. remove package lirc-modules-source
2. install kernel-source
3. checkout lirc cvs
[http://www.lirc.org/cvs.html](http://www.lirc.org/cvs.html)
4. follow howto from user "e9hack" in posting 12 from here 
[http://vdrportal.de/board/thread.php?postid=738978&sid=65ba1a254a8ab4ba841ff5c4c85c59e2](http://vdrportal.de/board/thread.php?postid=738978&sid=65ba1a254a8ab4ba841ff5c4c85c59e2)
(replace lirc_serial.c in the howto with the module you need eg. lirc_atiusb.c) 
5. build kernel
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

