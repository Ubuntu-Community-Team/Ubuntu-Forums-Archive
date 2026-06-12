---
title: "getting linux-restricted-modules"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by gmhafiz on 2008-05-04
Hi,

I compiled the vanilla kernel 2.6.25.1
```
$ uname -a
Linux gmhafiz-desktop 2.6.25.1 #1 SMP Sun May 4 13:03:14 IST 2008 i686 GNU/Linux
```

However, I cannot switch on compiz fusion, I use an nvidia graphic card. When I click on Restricted Drivers Manager, it says "You need to install the package linux-restricted-modules-2.6.25.1 for this program to work"


How do I compile a restricted module for my kernel?

---

### Post by Pumalite on 2008-05-04
sudo aptitude install linux-restricted-modules-`uname -r´

---

### Post by gmhafiz on 2008-05-04
> **Pumalite said:**
> sudo aptitude install linux-restricted-modules-`uname -r´

Since I am using kernel 2.6.25.1, it's restricted-modules would not be in the repository.

```
$ sudo aptitude install linux-restricted-modules-2.6.25.1
[sudo] password for me:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "linux-restricted-modules-2.6.25.1"
The following packages are unused and will be REMOVED:
  nautilus-actions python-qt3 python-sip4 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 23.5MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.

```

---

