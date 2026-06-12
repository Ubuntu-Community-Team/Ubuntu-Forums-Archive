---
title: "Linux kernel update FAIL"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by g33k-g33k on 2011-06-02
Hi, I tried to update Linux kernel (2.6.39) but after installation procedure PC won't boot into NEW kernel, I get only BLANK screen, but hopefully older kernel works just fine (2.6.38-9), do someone know what is causing that? And how to fix it, that I can fluently boot into 2.6.39?

Cheers

---

### Post by tommcd on 2011-06-02
How did you upgrade to the 2.6.39 kernel? The 2.6.39 is not part of the stock Ubuntu 11.04. 
Note that Ubuntu uses a heavily patched version of the Debian kernel. Note also that the Debian kernel is also heavily patched. So Ubuntu patches an already patched kernel. Unless you can apply all of those patches you will likely have problems.
The easy way to get updated kernels for Ubuntu is to install them from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
And for 2.6.39: The newest 2.6.39 kernel is still in RC stage: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/)

---

### Post by g33k-g33k on 2011-06-02
Here I found a tip for installing Linux kernel 2.6.39 on Ubuntu 11.04

[http://www.addictivetips.com/ubuntu-linux-tips/how-to-update-ubuntu-11-04-kernel-to-2-6-39-0/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-update-ubuntu-11-04-kernel-to-2-6-39-0/)

BTW I have followed this procedure, and as I see on [www.kernel.org](www.kernel.org) - latest version is 2.6.39 too, so this means that I must stay on older kernel versions?

---

### Post by tommcd on 2011-06-02
Obviously, that tutorial did not work.
Unless you have a burning need to use the latest and (hopefully!!) greatest kernel, I would suggest that you stick with the stock Ubuntu kernels that the Ubuntu repos provide.

---

### Post by g33k-g33k on 2011-06-02
Thanks, I have removed 2.6.39 and I am on stocked 2.6.38-9

---

