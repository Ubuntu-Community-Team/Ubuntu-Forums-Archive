---
title: "Kernel Source Files Help"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by andrew.pope on 2007-10-27
When I try to install the drivers for my RTL8187 WLAN Card. (USB)

```

make -C /lib/modules/2.6.10-5-386/build
 M=/root/desktop/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory. Stop.

```

I read somewhere that I need the kernel source files? What does this mean and furthermore, how do I accomplish this?

thanks in advance?

cheers

andy

---

### Post by Seisen on 2007-10-27
```
sudo apt-get install linux-source-2.6.15
``` or install the linux-source-2.6.15 package in synaptic

---

### Post by andrew.pope on 2007-10-27
what does the command sudo do?

and

I am upgrading to 7.10 now and leaving Hoary Hedgehog behind! What command would I use then?

thanks in advance!

cheers!

andy

---

