---
title: "Wireless connectivity"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by apperrault on 2010-04-09
Hi everyone,
I have an HP Mini 1151nr.  I just installed UNR 9.10.  I love this distro, and i have it on multiple other laptops, but for some reason, i cannot get the wireless to work.  I have read through a lot of the other posts, but i am totally confused on how to get both the wireless and the embedded Verizon card to work.  A lot of the other posts say to uninstall the b43 driver, but i dont see that it is installed.  Can anyone help.  Unfortunately, i am not tell that well versed on Linux, so step by step instructions would be greatly appreciated.

Thanks much

app

---

### Post by khelben1979 on 2010-04-11
```
sudo apt-get install wicd
```
will install **wicd** on your system. It's a good start in my opinion. [Wicd]("http://en.wikipedia.org/wiki/Wicd") is a wireless connection daemon.

```
man wicd
``` gives you some documentation for it.

---

