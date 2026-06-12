---
title: "[SOLVED] Updating my Kernel in 8.04 ?"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by covert on 2008-10-03
I have a SB600 southbridge and it is causing me problems on USB with  my current kernel 2.6.24-16-generic

I am looking to upgrade to a newer kernel like 2.6.27 to try to solve the problems with the USB on the SB600.

I cannot see anything newer than 2.6.24-19 in Synaptic.

What is the best way for me to go about upgrading the kernel to something newer ?

Current installation is Mythbuntu 8.04 with 2.6.24-16-generic kernel.

---

### Post by zvacet on 2008-10-03
Maybe [this]("http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html") is what are you looking for.

---

### Post by covert on 2008-10-03
I ended up adding intrepid to apt and then installing 2.6.27-4-generic. The changes the installer wanted to do the menu.conf looked odd so I did them by hand. Currently booted into 2.6.27-4-generic and just trying to get nvidia drivers working. My TV tuners all seems to be working fine. So far looking good.


nano /etc/apt/sources.list
```
deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe multiverse main restricted

```

---

### Post by covert on 2008-10-03
Unfortunatly this does not solve my problem with the USB on the SB600 falling out when it is loaded up with traffic. This 780G motherboard is going to the scrap heap.

---

