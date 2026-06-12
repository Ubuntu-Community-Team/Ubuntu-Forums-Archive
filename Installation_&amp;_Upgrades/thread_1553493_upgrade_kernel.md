---
title: "upgrade kernel"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by PeterKogler on 2010-08-15
If I would like to update my kernel to linux 2.6.34 on my asus eee 1001px laptop. How can I do that in the easiest way? I already downloaded the kernel from kernel.org.

---

### Post by kerry_s on 2010-08-15
just use the ppa:
[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

---

### Post by xangua on 2010-08-15
this PPA besides upgrading to the latest kernel version, it qalso improves intel & ati graphics performance

---

### Post by xangua on 2010-08-15
ups forgot to add the ppa :s

[https://launchpad.net/~guido-iodice/+archive/best-intel](https://launchpad.net/~guido-iodice/+archive/best-intel)

---

### Post by PeterKogler on 2010-08-16
sorry, i might be stupid but I do not understand how to install this kernel. I am totally new with linux. And suppose I would like to update a kernel on a computer that does not have internet yet because I can't get the wireless working without the new kernel. Please write simply about how to install the kernel in this situation,
Thanks for all help.
// Peter

---

### Post by pjalegria on 2010-08-16
What are the major diferences of this new kernel?

thx

---

### Post by IcarusR on 2010-08-16
Can you not connect with ethernet cable ?

See post 3 on this thread to get your wireless working if ehernet connection works...

[http://ubuntuforums.org/showthread.php?t=1479058]("http://ubuntuforums.org/showthread.php?t=1479058")

---

### Post by kerry_s on 2010-08-16
> **PeterKogler said:**
> sorry, i might be stupid but I do not understand how to install this kernel. I am totally new with linux. And suppose I would like to update a kernel on a computer that does not have internet yet because I can't get the wireless working without the new kernel. Please write simply about how to install the kernel in this situation,
Thanks for all help.
// Peter


a stock install does not have the stuff to build a kernel.
you need a ubuntu kernel. download this:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb)

get it on your laptop & double click on it to install.

---

