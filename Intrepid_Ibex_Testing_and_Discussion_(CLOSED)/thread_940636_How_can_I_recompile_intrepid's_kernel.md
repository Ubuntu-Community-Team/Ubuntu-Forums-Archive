---
title: "How can I recompile intrepid's kernel?"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by patrickfromspain on 2008-10-07
Hi there,

I've installed the linux-source-2.6.27 package and now I want to recompile it enabled the pci-express power savings. I'd also like to patch it with phc and tux on ice, but I've not done it yet, so I only have the original source.

I do make oldconfig, then make xconfig and finally make-kpkg clean and there I get this error:

```

patrick@patrick-laptop:~/Escriptori/linux-source-2.6.27$ sudo make-kpkg clean
exec make -f /usr/share/kernel-package/ruleset/minimal.mk clean 
====== making target minimal_clean [new prereqs: ]======
Cleaning.
test ! -f .config || cp -pf .config config.precious
test ! -e stamp-building || rm -f stamp-building
test ! -f Makefile || \
            make    ARCH=xen distclean
make[1]: Entering directory `/home/patrick/Escriptori/linux-source-2.6.27'
Makefile:528: /home/patrick/Escriptori/linux-source-2.6.27/arch/xen/Makefile: No such file or directory
make[1]: *** No rule to make target `/home/patrick/Escriptori/linux-source-2.6.27/arch/xen/Makefile'.  Stop.
make[1]: Leaving directory `/home/patrick/Escriptori/linux-source-2.6.27'
make: *** [minimal_clean] Error 2

```

I've always compiled kernel succesfully this way, any ideas?

UPDATE: bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280173)

---

