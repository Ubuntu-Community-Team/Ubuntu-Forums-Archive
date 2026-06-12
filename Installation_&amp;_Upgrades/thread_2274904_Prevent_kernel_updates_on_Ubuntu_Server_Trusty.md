---
title: "Prevent kernel updates on Ubuntu Server Trusty"
date: 2015-04-23
forum: Installation &amp; Upgrades
---

### Post by gurabli on 2015-04-23
Hi,

I'm running Ubuntu Server Trusty as a home media server, and it also has a DVB-S2 USB card. However, the driver for the DVB card is not supported (yet), so I need to compile the driver each time the kernel is upgraded. This takes quite a lot of time, and I would really like to avoid this. I'm aware of the potential risk of not applying kernel updates, but I will do a regular update once in a while and recompile the driver.

I read a lot about how to pin the packages, but not all the posts were informative enough. It is also not clear exactly what I need to pin. One post list the following: [COLOR=#000000]To pin kernel version you'd have to lock linux-generic, linux-image-generic, linux-headers-generic and linux-restricted-modules-generic.

Is this correct? If yes, please could you guide me how to do this step-by-step, and then how to unpin them if I would like to upgrade?

Thank you![/COLOR]

---

### Post by dino99 on 2015-04-23
There is a meta-package named 'linux-generic' which can be purged (sudo apt-get purge linux-generic). You then will not be proposed to upgrade/install new kernel
But the real solution will be to get a kernel version handling directly that driver (module); maybe it already has been integrated into one of the latest upstream kernel (not listed into Trusty archive); note that Vivid is ready to be released, even if its not an LTS its way better than Trusty. Why not upgrading as the LTS's only offer a false benefit ?

Is that driver been requested by opening a linux bug report ?

---

### Post by gurabli on 2015-04-23
Thank you for your answer!
So I just need to type the following:

sudo apt-get purge linux-generic

And this will prevent any further kernel updates? I'm not exactly sure what will this do, so unless I decide to upgrade the kernel, it will remain the version currently installed?

The DVB-S card I use is the DVBSky S960 [http://www.linuxtv.org/wiki/index.php/DVBSKY_S960](http://www.linuxtv.org/wiki/index.php/DVBSKY_S960)
According to the wiki, support in-kernel is expected in Linux kernel 3.18. I'm not sure about the kernel version of Vivid and if the driver is already included or not. 
I'm also not sure how to request a driver, or if this had been done already. I'm stuck with the compiling the driver each time a kernel update is released, and that happens quite often.

---

### Post by dino99 on 2015-04-23
that driver is included since kernel 3.18. Vivid is released with the next 3.19 one (so have it implemented too).
[https://lkml.org/lkml/2014/10/9/382](https://lkml.org/lkml/2014/10/9/382)

linux-generic is a 'meta-package' to get the default list kernel packages, nothing else. Like all the meta-package they can be removed without changing the existing installation.

---

