---
title: "Kernel 3.7 in 12.10/Quantal, how?"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by ThomasNovin on 2012-11-27
Can't find any good information on how to install kernel 3.7 in Ubuntu 12.10/Quantal.

I know of [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) but there are no complete kernels for 12.10 (rc2 exists but is missing kernel headers for -all).

Rgds

---

### Post by ThomasNovin on 2012-12-18
After discussing with some Ubuntu kernel developers on IRC I learned that it's not important that those kernel are for Raring.

They can fit just as good with Quantal (or Precise), just that if you have any DKMS-modules it's not certain that they can be compiled.

So I installed 3.7.1 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) with sudo dpkg -i *.deb

linux-headers-3.7.1-030701_3.7.1-030701.201212171620_all.deb
linux-headers-3.7.1-030701-generic_3.7.1-030701.201212171620_i386.deb
linux-image-3.7.1-030701-generic_3.7.1-030701.201212171620_i386.deb
linux-image-extra-3.7.1-030701-generic_3.7.1-030701.201212171620_i386.deb

I noted in the console that nvidia module could not be compiled. Found that it works in newer versions so I upgraded by using xorg-edgers ppa.

With nvidia-current 313.09-0ubuntu1~xedgers~quantal1 it could be compiled. 

Then rebooted and 3.7.1 works perfectly!

---

### Post by ashjas on 2013-01-08
@ThomasNovin Thanks. Your solution worked perfectly for me aswell.
i am on ubuntu 12.04 precise..

earlier by using this link to upgrade:[http://www.upubuntu.com/2012/12/install-linux-kernel-371-on-ubuntu.html](http://www.upubuntu.com/2012/12/install-linux-kernel-371-on-ubuntu.html)

i ended up in booting ubuntu fine.. but my keyboard and mouse stopped working..

Thanks so much..

---

### Post by ThomasNovin on 2013-02-26
I'm now on 3.8.

The driver for nvidia to use is now nvidia-313 instead of nvidia-current.

---

