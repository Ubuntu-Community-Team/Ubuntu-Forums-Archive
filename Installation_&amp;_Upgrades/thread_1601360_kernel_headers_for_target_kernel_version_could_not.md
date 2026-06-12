---
title: "kernel headers for target kernel version could not be found"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by eewoud on 2010-10-20
I get the following error message trying to install dazuko on xubuntu 10.04: "headers for target kernel version could not be found"
But when I run sudo apt-get install linux-headers-$(uname -r), I get the message that I already installed the headers.
My current kernel is 2.6.34-020634-generic

How can I install dazuko withouth having this problem??

---

### Post by searchfgold6789 on 2010-10-20
Maybe the program is checking for _earlier_ headers than the ones you have. I come across this lot.

---

