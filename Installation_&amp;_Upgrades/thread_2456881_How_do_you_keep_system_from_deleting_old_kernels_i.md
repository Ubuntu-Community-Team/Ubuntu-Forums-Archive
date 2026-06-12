---
title: "How do you keep system from deleting old kernels in 20.04"
date: 2021-01-21
forum: Installation &amp; Upgrades
---

### Post by keep-tryin on 2021-01-21
After needing to boot back to the 5.4.0-59-generic kernel to have a working desktop after one of my computers updated to the 5.8 kernel I would like to set it so it keeps all old kernels. Is there a way to do this?
Also is there away to reinstall a 5.4 kernel on a machine that updates to 5.8 and has erased the 5.4 kernel version I see that synaptic lists 5.4 kernels but not sure how to choose the right one and what dependencies I would need
             Thanks
              Linda

---

### Post by CatKiller on 2021-01-21
If you have the linux-generic package installed you'll keep your 5.4 branch kernels, and get security updates to them. You're getting 5.8 branch kernels because you've got the HWE package installed, which brings in kernels from later Ubuntu releases.

---

### Post by grahammechanical on 2021-01-21
Software Updater runs 3 commands - update; upgrade and autoremove. If we use the terminal and only run update and upgrade no old kernels will be removed. But be careful, the next time we run Software Updater it will remove old kernels if we let it.

As for Synaptic. Note the naming convention for Linux kernels: 5.4.0-62. The last two numbers show the order of the kernels. Search Synaptic for a Linux kernel, select one, preferably the one with the highest last two numbers and allow Synaptic to mark all packages that are dependent or related to that choice of kernel. There are several parts to what we call the kernel. We need all of them.

Regards.

---

