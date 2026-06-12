---
title: "Ubuntu + firestarter impossible?"
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by Scorper on 2005-06-15
I tried installing firestarter to my ubuntu server but it's not working. It start to roll off errors to the console:

Error reading /proc/net/ip_conntrack: No such file or directory
Error reading /proc/net/ip_conntrack: No such file or directory
Error reading /proc/net/ip_conntrack: No such file or directory

 and firestarter says "Device eth0 not ready, please check that your internet connection is active blablabla..."

Running on Ubuntu Hoary and 2.6.10-5 kernel.

What can I do about this??

---

### Post by alastair on 2005-06-15
1) Do you have a working network interface e.g. perhaps eth0?

ifconfig -a

2) Is "iptables" installed?

---

### Post by desdinova on 2005-06-15
Perhaps have a look at Shorewall instead?

---

