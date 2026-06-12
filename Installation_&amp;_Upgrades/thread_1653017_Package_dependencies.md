---
title: "Package dependencies"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by leomyster on 2010-12-26
Hello All,

I just installed ubuntu 10.04 LTS on my Acer Aspire 5745. The installation was successful. However, I found that my internet is not working. Later I realised that there are no ethernet drivers. The one that I need is Atheros AR8151 PCI-E Gigabit Ethernet controller(NDIS 6.20). My wireless is also not working. This one is a Broadcom 802.11n Network adapter. 
On googling, I found this thread : [http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)

To install the driver first, I had to do build-essential and headers-generic. Since I have a desktop, i thought of manually downloading the packages on my desktop and then transferring it to the acer. But i came across many dependencies for build-essential, that is, I first had to install something else before build-essential. The dependencies led me to further dependencies and so on. Is there any way for me to get all the packages without downloading each individual ones? Or is there a simpler way to do this?

Regards,
Mithun

P.S. This post is also apt for "Absolute Beginner Talk" since I am new to linux itself.

---

### Post by dino99 on 2010-12-26
[http://tuxthink.blogspot.com/2010/08/enabling-atheros-ethernet-controller-on.html](http://tuxthink.blogspot.com/2010/08/enabling-atheros-ethernet-controller-on.html)

or you can watch (not so simple):

here is an example on Fedora, so you need to replace "yum" which is a Fedora command, by "sudo apt-get" on ubuntu

[http://rhythmcloud.blogspot.com/2010/07/how-to-install-ar8151-v10-gigabit.html](http://rhythmcloud.blogspot.com/2010/07/how-to-install-ar8151-v10-gigabit.html)

---

### Post by leomyster on 2010-12-26
Hello dino99,

Thanks a bunch. Did exactly what was instructed in the first link that you provided. Got some errors while extracting the drivers. Ignored it. After that, things just fell in place. Thanks again.

Best Regards,
Mithun

---

