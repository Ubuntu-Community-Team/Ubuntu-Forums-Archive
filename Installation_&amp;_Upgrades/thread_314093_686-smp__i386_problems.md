---
title: "686-smp / i386 problems"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by charles.g.moore on 2006-12-07
When I install the linux-686-smp kernel headers synaptic tells me that I need to also get the i386 headers is that right?

I am having problems installing programs through automatix and easyubuntu due to apt-based errors and believe that it has something to do with the header info.

Am I way off base? (wouldnt be the first time)

Do i need the i386 things and if not how do I tell synaptic not to remind me of them?

---

### Post by mcduck on 2006-12-07
if you are running 686 kernel and it works fine, you can just uninstall the 386 kernel and other packages related to it.

---

### Post by zgornel on 2006-12-07
If packages require the kernel-headers, install them. They are useful also if you want to compile a program yourself. I do not remeber very well the Dapper situation but kernel headers are independent to the type of kernel (i386/i686), they're just .h files.

---

### Post by mcduck on 2006-12-07
yeah, the right way to install kernels is not to pick the kernel version you want, but instead install one of the kernel metapackages, linux-386, linux-k7, linux-686-smp etc.

These packages always depend on latest version of kernel, headers and modules so having the metapackage makes sure that you'll get automatic updates for all kernel-related files on your system. Saves you from lots of troubles ;)

---

