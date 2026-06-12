---
title: "kernel and packages dependency, general question"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by al2222 on 2010-03-14
I have only little experience with system administration.

I installed Ubuntu 9.10 from Windows on notebook Compaq 6715s. It came with kernel 2.6.31-14-generic. After every update of system containing a kernel, the new kernel doesn't work. So I use the 2.6.31-14, I don't update kernel and I am happy. (Once I tried to compile kernel but it didn't work.) 

Is it possible that I update some package and the package will not work with my old kernel? Is it solved by dependencies?

Thanks, Alex

---

### Post by zvacet on 2010-03-15
>  After every update of system containing a kernel, the new kernel doesn't work

Does this mean you can not boot in new kernel or some software doesn't work with new kernel.Did you get any errors during install of new kernel?

---

### Post by slakkie on 2010-03-15
You can keep your olde kernel without having to worry about dependencies.. 

```

     2.6.24.27.29 0
        995 http://security.ubuntu.com hardy-security/main Packages
        995 http://archive.ubuntu.com hardy-updates/main Packages
 *** 2.6.24.26.28 0
        100 /var/lib/dpkg/status
     2.6.24.16.18 0
        990 http://archive.ubuntu.com hardy/main Packages

```

As you will see here, I'm just in between kernels for Hardy, and have no issues. You don't need to update the kernel, you can keep it as is.

---

### Post by al2222 on 2010-03-20
> **zvacet said:**
> Does this mean you can not boot in new kernel or some software doesn't work with new kernel.Did you get any errors during install of new kernel?

Yes, I cannot boot in new kernel. The booting process stops in Grub shell, so I must boot  2.6.31-14 kernel, uninstall new one and update grub.

There is update manager which one per week offer me new updates. I have never seen any error after the manager finished an update. The problem was after reboot. I am not linux expert and I don't know where I can search error. I tried to compile kernel but compiled kernel didn't work.

The question is if the kernel 2.6.31-14-generic will work after every update of other parts of system.

---

