---
title: "Couldnt connect to net using mozilla"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by shajip88 on 2010-05-08
hi i was using ubuntu 9.10 installed as a program inside windows. i clicked the upgrade button in my update manager and the ubuntu upgraded to 10.04. Now i couldnt access net from mozilla. my updates are still working and i can download those. when i type the address in mozilla and press enter it says connecting and then says to check my network settings. help me please. this is the case in both my acer laptop and my desktop

---

### Post by lemming465 on 2010-05-09
When you say "ubuntu ... installed ... inside windows", do you mean
a) WUBI install, where there is a C:\ubuntu folder on your disk, an ubuntu item in your windows boot menu, and you boot native ubuntu instead of windows

b) virtual guest install, booting windows first, then running a hypervisor such as vmware or virtualbox or hyper-V and booting ubuntu as a guest operating system

Solutions to your problem can be different depending; I'll assume (a), the WUBI install case.

If updates are working but mozilla firefox is having trouble, the first suspect is bad DNS settings, and the likely culprit is lack of a DNS server in /etc/resolv.conf.  Can you show us the results of:```
ping -c2 8.8.8.8
dig @8.8.8.8 www.wisc.edu
dig www.wisc.edu
cat /etc/resolv.conf
ip address show
```
If the "dig @" works and the plain "dig" doesn't, then your problem is almost certainly with /etc/resolv.conf.  This file tends to get rewritten by NetworkManager on each boot or network connection change, so it may take some further troubleshooting to get you a permanent solution.  A quick workaround is to put at least one nameserver into /etc/resolv.conf by hand. 8.8.8.8 is a google nameserver, e.g. ```
sudo -i
echo "nameserver 8.8.8.8" >> /etc/resolv.conf
```

---

