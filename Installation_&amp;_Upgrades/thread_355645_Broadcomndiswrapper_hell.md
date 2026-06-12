---
title: "Broadcom/ndiswrapper hell"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by ziphead on 2007-02-07
Hi,

I installed Dapper, then got ndiswrapper to work by downloading and compiling the source after installing build-essential.

The problem I have now is that no-how-no-way can I make ndiswrapper work.  If I install the ndiswrapper-utils and ndiswrapper-common packages, modprobe complains about a missing ndiswrapper.ko.  If I compile from source, then it complains about some magic key string being wrong.  Apparently, linux-image-2.7.10-generic is compiled with gcc 4.1 and I'm working with gcc 4.0 right now.

So, I see that I have 2 choices:

1. Download, compile and install the kernel source using the gcc I have.
2. Find a package with the appropriate ndiswrapper.ko in it, if it exists.

It would be simpler to do the second if possible.  I've compiled kernels before, but I'm afraid of not downloading the appropriate packages, getting home and finding out that I'm missing stuff.  Right now, I have no internet access unless I have the wireless working, and all I can do right now is download .debs onto my USB key at work and hope for the best.

So, my questions are:

A. What packake has the ndiswrapper kernel module?
B. Have I missed something?

Thanks,

ziphead

---

### Post by ziphead on 2007-02-08
Problem solved.

It turns out that the ndiswrapper that ships with Dapper and Edgy can't deal with a unified driver that supports both 32 and 64 bit versions of Windows.  This is a shame, since HP is shipping all those nice Turion/Nvidia laptops for so cheap. 

I ended up reinstalling Dapper, and making ndiswrapper from source (1.37).  You have to rename the ndiswrapper.ko that ships with the kernel.  I guess I will stay with Dapper, unless I decide to installing Edgy or Feisty from CD and doing the same thing.

Certainly you can't use the stock ndiswrapper package that comes with Dapper with the drivers that HP supplies for my laptop.

ziphead

---

