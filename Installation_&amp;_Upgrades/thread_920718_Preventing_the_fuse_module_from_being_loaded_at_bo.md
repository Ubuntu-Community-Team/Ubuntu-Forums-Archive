---
title: "Preventing the fuse module from being loaded at boot time?"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by Zack Perry on 2008-09-15
I am trying to prevent my Ubuntu 8.04 desktop (*running in a VirtualBox 2.02 VM with Windows XP SP3 Home as the host*) from loading the fuse module that comes bundled with the kernel:

root@ubuntu:~# uname -a
Linux ubuntu 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
root@ubuntu:~# dpkg -S /lib/modules/2.6.24-19-generic/kernel/fs/fuse
linux-image-2.6.24-19-generic: /lib/modules/2.6.24-19-generic/kernel/fs/fuse

I would like to load the latest stable (as of this writing) that I have built myself fuse-2.7.4

After several attempts, I must say that I don't see a clean way to prevent the fuse kernel module from loading at boot time.

I have done the following steps (additively):

   1. put  blacklist fuse in /etc/blacklist -> result: lsmod still shows fuse  50708 3
   2. mv  /etc/modprobe.d/fuse  /root -> result: lsmod still shows fuse  50708 3
   3. mv /lib/modules/2.6.24-19-genereic/kernel/fs/fuse / -> result: lsmod still shows fuse  50708 3
   4. comment out the line with fuse.ko in /lib/modules/2.6.24-19-generic/modules.dep -> Result: lsmod still shows fuse  50708 3

I would appreciate a hint about the right way to accomplish my goal.

Thanks,

--Zack

---

### Post by Zack Perry on 2008-09-15
I found the answer:

[http://wiki.debian.org/Modules](http://wiki.debian.org/Modules)

--Zack

---

