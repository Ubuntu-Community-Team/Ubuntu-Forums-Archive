---
title: "How to upgrade Kernel from 3.13 to 3.16 on Ubuntu 14.04.2 LTS server"
date: 2015-08-01
forum: Installation &amp; Upgrades
---

### Post by fedtobunt on 2015-08-01
When I upgraded from Ubuntu server 12.04 LTS to Ubuntu 14.04.02 LTS Server, the kernel updated to 3.13 but not 3.16. 
I require kernel 3.16 to support a Hauppauge TV tuner card.  
How do I update the the Linux Kernel to version 3.16 on in Ubuntu 14.04.2 LTS _**server**_ the easy way without having to rebuild the kernel? Is there a guide?

 
```
Linux NAS1 3.13.0-57-generic #95-Ubuntu SMP Fri Jun 19 09:28:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

```

Distributor ID: UbuntuDescription:    Ubuntu 14.04.2 LTS
Release:        14.04
Codename:       trusty

```

---

### Post by v3.xx on 2015-08-01
I am sticking with the 3.13 kernel, but found this.

[http://ubuntuforums.org/showthread.php?t=2266369&p=13232819#post13232819](http://ubuntuforums.org/showthread.php?t=2266369&p=13232819#post13232819)

---

### Post by fedtobunt on 2015-08-02
Yes I came across that post but it might be for the Ubuntu desktop version not server version. I don't need the GUI.
I don't have an option if I want this TV tuner card to work, it needs to be 3.16.
See here:
[http://www.hauppauge.com/site/support/linux.html](http://www.hauppauge.com/site/support/linux.html)

I want to keep to the official flavor of ubuntu if possible because I don't want to spend time debugging later.

---

### Post by dino99 on 2015-08-02
kernels are kernels; only choose the one for your arch

---

### Post by fedtobunt on 2015-08-03
> **dino99 said:**
> kernels are kernels; only choose the one for your arch
This is not very helpful.

---

