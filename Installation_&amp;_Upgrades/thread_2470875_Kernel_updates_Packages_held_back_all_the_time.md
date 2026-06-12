---
title: "Kernel updates: Packages held back all the time"
date: 2022-01-14
forum: Installation &amp; Upgrades
---

### Post by cryptochrome242 on 2022-01-14
Hello,

whenever I do an apt-get upgrade and there are new kernel packages, apt seems to hold them back:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic-hwe-20.04 linux-headers-generic-hwe-20.04 linux-image-generic-hwe-20.04

```

I know how to install the held back packages, but this is happening consistently with every single kernel update. Why is that and is there anything I can do to fix this?

Thanks

---

### Post by deadflowr on 2022-01-14
the *apt-get upgrade* command does not install new packages, which kernel upgrades always are.
To install new kernels and other new packages run one of these commands
```
sudo apt-get dist-upgrade
sudo apt upgrade
sudo apt full-upgrade
```

running 
```
man apt-get 
man apt
``` will explain what all those do.

Note that
```
sudo apt upgrade
``` differs from what
```
sudo apt-get upgrade
``` is

---

### Post by cryptochrome242 on 2022-01-14
> **deadflowr said:**
> the *apt-get upgrade* command does not install new packages, which kernel upgrades always are.


Perfect. Thank you for explaining! :)

---

