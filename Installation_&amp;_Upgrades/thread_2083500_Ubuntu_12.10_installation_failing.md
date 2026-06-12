---
title: "Ubuntu 12.10 installation failing"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by xbobby_bobx on 2012-11-12
When I try to install Ubuntu the installation process goes fine, till it reaches the end and it through this error message "? kthread_freezable_should_stop+0x60/0x60" and it freezes the whole installation and I have to hard reset my laptop to reboot.. My guess is my GPU is not being recognized or something.

My hardware:

AMD athlon x64

Ubuntu 12.10 32 bit

ATI Radeon X1200

WUBI installation.

Anyone knows how to solve it?

---

### Post by bcbc on 2012-11-13
Boot with nomodeset: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I'd guess that your grub menu is already setup, so select Ubuntu and immediately hold the SHIFT key to pop the grub menu. Then edit the first entry as shown in the thread I linked above (the first post even though it says not for wubi).

If that doesn't work, then there are some wubi specific steps in post #8 of that thread for the 'first boot' after installing Wubi as this is different.

---

### Post by xbobby_bobx on 2012-11-13
Not sure if that is going to work.. I'm trying the 64 bit and will see if it will pass the kernel crash.

---

### Post by xbobby_bobx on 2012-11-13
It worked with the 64 bit.. Although it became really laggy so I removed it.. Thank you for the help anyway.

---

