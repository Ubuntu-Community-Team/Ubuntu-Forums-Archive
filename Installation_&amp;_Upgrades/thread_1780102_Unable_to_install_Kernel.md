---
title: "Unable to install Kernel"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by by100 on 2011-06-11
Hello all!
I have this very annoying problem with my netbook:
I have an Asus Eee Pc 1001PX and every-time I try to connect it to a wireless network, the Netbook Freezes totally, giving me no other choice than hand-forcing shutdown.
I tried this thread:
[http://ubuntuforums.org/showthread.p...=eee+pc+1001px](http://ubuntuforums.org/showthread.p...=eee+pc+1001px)
But I can't do this:

> he problem is with the kernel in 11.04, seems to include all newer asus eeepc's and is solved in latest kernel.
to solve that you can download the latest kernel and install it very easily;
go to 
[http://kernel.ubuntu.com/~kernel-ppa...daily/current/](http://kernel.ubuntu.com/~kernel-ppa...daily/current/)
and download the files; 

linux-headers-2.6.39-999_2.6.39-999.201105191210_all.deb
linux-headers-2.6.39-999-generic_2.6.39-999.201105191210_i386.deb
linux-image-2.6.39-999-generic_2.6.39-999.201105191210_i386.deb

(or different versions depending on time) then install them in exactly same order by the command;

sudo dpkg -i filename

one after the other, then restart the netbook. it worked perfectly for me.
When I try to install the third file I get this error:

> dpkg: dependency problems prevent configuration of linux-image-3.0.0-999-generic:
linux-image-3.0.0-999-generic depends on module-init-tools (>= 3.13-1ubuntu1); however:
Version of module-init-tools on system is 3.12-1ubuntu6.
dpkg: error processing linux-image-3.0.0-999-generic (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
linux-image-3.0.0-999-generic

I use the 11.04 Ubuntu.
What can I do?
Thanks a lot,
Barak.

---

### Post by dhave-dhave on 2011-06-14
You can find a newer modules-init-tools package here:

[https://launchpad.net/ubuntu/oneiric/amd64/module-init-tools/3.13-1ubuntu1](https://launchpad.net/ubuntu/oneiric/amd64/module-init-tools/3.13-1ubuntu1)

Use at your own risk, though, since you just might break something else.

---

