---
title: "How do I install Ubuntu without nouveau driver? - Fresh installation"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by ncsuchess on 2012-04-28
Hi

Yup, I am hitting this issue like many others due my Gigabyte GeForce GTX 550 card. 

I did come across many threads where people suggest blacklisting those modules etc and installing proprietary Nvidia drivers. However I am not reaching to that stage.

As soon as Ubuntu flash screen pops up, it results in kernel panic and the boot process hangs after enumerating disk drives. The kernel dump and stack trace is pointing to nouveau driver. This is the fresh installation of Ubuntu. Is there any way to 'force' Ubuntu to use bare minimum basic VGA drivers to be able to complete installation? This way, once up and running, I can install the actual drivers.

I have tried installing Ubuntu under Windows and selecting 'Demo' 'basic graphics' modes but it is still trying to load nouveau drivers.

Thanks in advance
****

---

### Post by jawilljr on 2012-04-28
Try to turn on [nomodeset](http://ubuntuforums.org/showthread.php?t=1613132)

Jerry

---

### Post by ncsuchess on 2012-04-28
Hi Jerry

That worked. Thanks a lot!

---

