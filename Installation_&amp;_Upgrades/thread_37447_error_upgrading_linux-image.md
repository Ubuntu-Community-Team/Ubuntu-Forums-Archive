---
title: "error upgrading linux-image"
date: 2005-05-27
forum: Installation &amp; Upgrades
---

### Post by kozmo on 2005-05-27
I was able to install just fine and get wireless networking up and running using the [Setup ndiswraper Howto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto/view?searchterm=ndiswrapper) 

But when I tried to upgrade my packages by clicking the notification icon on the taskbar I get an error when upgrading the package: linux-image-2.6.10-5-386.

The following problems were found on your system:

E:/var/cache/apt/archives/linux-image-2.6.10-5-386_
2.6.10-34.1_i386.deb: trying to overwrite '/lib/
modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/
ndiswrapper.ko' which is also in package ndiswrapper-
modules-2.6.10-5-386

Any suggestions on how to fix this problem?

---

### Post by K2712 on 2005-06-29
I'm having the exact same problem, does anyone know what the problem is?

---

### Post by Mysa on 2005-07-04
Hello, i got the same error. I solved it by uninstalling ndiswrapper and then upgrading the package.

---

