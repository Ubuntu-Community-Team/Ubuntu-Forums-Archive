---
title: "Loss of Trackpad function"
date: 2019-12-04
forum: Installation &amp; Upgrades
---

### Post by Rex Bouwense on 2019-12-04
I have Lubuntu 18.04.3 installed on my Dell Inspiron 14-3452 laptop and I have been cruising dumb, fat, and happy for several years until the release of kernel 4.15.0-72.  Since I use a wireless mouse when I am at home I did not notice that my trackpad was no longer functioning until I attempted to use it outside of my home.  After research on the Internet and attempting various fixes, I thought perhaps I should check the kernel.  When I booted from a previous kernel ( 4.15.0-70) the trackpad function was restored.  While this is a work around is there a fix for the trackpad to enable me to use the current kernel for my distro.

---

### Post by mörgæs on 2019-12-06
I would expect 18.04.3 to run a kernel in the 5 series. Is the system fully updated?

---

### Post by Rex Bouwense on 2019-12-06
Yes the system is fully updated.  However, it was installed as 18.04 and that version uses the 4.15 kernel.  I don't believe the kernel is automatically upgraded as updates are released   A fresh install would of course be using 5.xx.

---

### Post by mörgæs on 2019-12-06
I have an 18.04 installed 2019-03-24. **Uname -a** gives 
```
5.0.0-37-generic #40~18.04.1-Ubuntu SMP Thu Nov 14 12:06:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

The difference is probably that I installed the .1 version back then. 

Anyway, it seems like a bug has been introduced into an old kernel. Have your tried a live boot of a newly downloaded 18.04.3 / 19.10 for comparison?

---

### Post by Rex Bouwense on 2019-12-06
Yesterday I had booted with a live Ubuntu 18.04.3 and this morning I just booted with a live Lubuntu 18.04.3 and the trackpad functions as it should.  So apparently I have a choice of 1. reinstalling Lubuntu. 2. Installing a 5.xx linux kernel. or 3. Continue to use the 4.15.0-70 kernel until a new update is released.

---

### Post by mörgæs on 2019-12-06
If you go for 2) then the command is
```
sudo apt install linux-generic-hwe-18.04 xserver-xorg-hwe-18.04
```

---

### Post by Rex Bouwense on 2019-12-06
Gracias

---

### Post by Rex Bouwense on 2019-12-13
FYI there is a bug report filed:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1854798](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1854798)

---

