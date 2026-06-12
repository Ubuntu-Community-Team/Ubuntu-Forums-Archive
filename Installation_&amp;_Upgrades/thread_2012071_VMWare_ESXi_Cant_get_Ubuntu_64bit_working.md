---
title: "VMWare ESXi: Cant get Ubuntu 64bit working"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by trauner on 2012-06-28
Hi there!

I've installed Ubuntu-12-AMD-64bit a few hours ago on my freshly new installed VMWare Esxi Machine (V.5). The Host itself supports 64bit architecture but if i try to install Ubuntu 64-Bit-Server Edition on that machine, after successful installation my ubuntu runs only on 32bit Mode. Whats going on here?

Any help would be nice.

Thanks in advance!

Console Output:
root@memcache001:~# uname -i
i386

root@memcache001:~# uname -a
Linux memcache001.xxxx 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux

---

### Post by Old_Grey_Wolf on 2012-06-28
From what you posted, it looks like you downloaded and installed a 32-bit version. 

Where did you download it from?

You may want to try downloading the 12.04 64-bit Server iso from [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)

---

### Post by trauner on 2012-06-29
Well i did an wget on [http://www.ubuntu.com/start-download?distro=server&bits=64&release=lts](http://www.ubuntu.com/start-download?distro=server&bits=64&release=lts)

and it downloaded me 64bit distro, but if i install ubuntu with this image i only get a 32bit system. this is really weird.

---

