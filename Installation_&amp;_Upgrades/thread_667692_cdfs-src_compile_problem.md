---
title: "cdfs-src compile problem"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by debbio on 2008-01-14
Hi at all,
i've downloaded cdfs-src but it was impossible to compile it  due to a some headers or files missing in the tarball(i surfed code,there are some items undeclared neither in the tarball nor in the linux-kernel source).
Does anyone of you knows an up to date version or a patched version for cdfs-src package?
thanks in advance.
Matteo

---

### Post by Defrector on 2008-03-15
I don't know if this is the same thing, but I'm just posting to second that there are some issues building cdfs-src in ubuntu 7.10 from the install done from apt. When attempting to 'sudo make', here is what happens:

```
:/usr/src/modules/cdfs/2.6$ sudo make
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/usr/src/modules/cdfs/2.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/modules/cdfs/2.6/root.o
/usr/src/modules/cdfs/2.6/root.c: In function ‘cdfs_init’:
/usr/src/modules/cdfs/2.6/root.c:598: error: ‘CLONE_FS’ undeclared (first use in this function)
/usr/src/modules/cdfs/2.6/root.c:598: error: (Each undeclared identifier is reported only once
/usr/src/modules/cdfs/2.6/root.c:598: error: for each function it appears in.)
/usr/src/modules/cdfs/2.6/root.c:598: error: ‘CLONE_FILES’ undeclared (first use in this function)
/usr/src/modules/cdfs/2.6/root.c:598: error: ‘CLONE_SIGHAND’ undeclared (first use in this function)
make[2]: *** [/usr/src/modules/cdfs/2.6/root.o] Error 1
make[1]: *** [_module_/usr/src/modules/cdfs/2.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2

```

---

### Post by zvacet on 2008-03-15
Why don´t you install it from synaptic?

---

### Post by Defrector on 2008-03-15
Installing from synaptic just dumps source code into usr/src and doesn't actually install anything. I think that's why it is called "cdfs-src"

---

