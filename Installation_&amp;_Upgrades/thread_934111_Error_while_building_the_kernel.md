---
title: "Error while building the kernel"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by h3llh0l3 on 2008-09-30
Hello all,

I was trying to install VMWare and while running the config.pl it requested for the kernel source which I did not have. I tried looking for the source of the kernel that I have(2.6.24-19-server) but in vain. So I thought I would upgrade the kernel and then proceed with the installation of VMWare.

So I downloaded source for 2.6.26.5. When I try to build the kernel it gives me the following error:

```
Makefile:518: /usr/src/linux-2.6.26.5/arch/xen/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-2.6.26.5/arch/xen/Makefile'.  Stop.
make: *** [conf.vars] Error 2

```

I have never done this before, so I was unsure what it means.
Please let me know how can we fix it.

Thanks :)

---

