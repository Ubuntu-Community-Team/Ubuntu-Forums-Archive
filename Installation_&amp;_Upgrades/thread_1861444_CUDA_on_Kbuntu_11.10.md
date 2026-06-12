---
title: "CUDA on Kbuntu 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by phil128 on 2011-10-15
Hi all.

After a fresh install of Kbuntu 11.10 I installed the kernel-sources and headers, disabled nouveau via GRUB. Ran the Nvidia-development driver and I get this following error.
```

ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option. etc.. etc..

```


Now, I've heard someone on this forum saying you don't need the cuda-developer driver, but I'm studying CUDA programming at University, and I don't know if you need the dev-driver to compile and run CUDA programs. Previously, I ran CUDA with Ubuntu 10.04 and it was fine.

Kbuntu + Ubuntu comes with the Linux 3.0 kernel. I don't know if this is the issue.

Has anyone managed to get CUDA working with this distro, or with Linux 3.0?

Thanks.

---

### Post by GrantStoner on 2011-10-15
I'm also looking for info on this. Thanks.

---

### Post by phil128 on 2011-10-15
Hopefully someone will let us know.

---

### Post by MohammadElmi on 2011-10-23
I have not test it myself but there are threads in nvidia forums ([+]("http://forums.nvidia.com/index.php?showtopic=212998&st=0&p=1309992&#entry1309992") and [+]("http://forums.nvidia.com/index.php?showtopic=210678&view=findpost&p=1296540")) saying that there is no need to install developer driver on ubuntu 11.10. There is also an argue that building codes with some libraries does not work.

---

