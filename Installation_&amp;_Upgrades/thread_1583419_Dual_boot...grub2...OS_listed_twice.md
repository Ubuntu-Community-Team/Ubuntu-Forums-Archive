---
title: "Dual boot...grub2...OS listed twice?"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by michiganitis on 2010-09-27
Hello,

I just installed Ubuntu on my laptop on a separate partition as my Windows 7 OS. When it starts up, grub2 loads and asks me which OS to boot. In the list, it lists Ubuntu and Ubuntu (Recovery Console) twice. Each is listed two times.

Is this normal? Why is this?

Thanks!

---

### Post by oldfred on 2010-09-28
You have an upgraded kernel. Generally we recommend that you keep two kernels in grub so if the newest has any issues you can still boot the older one.

Uninstall extra kernels:-------------------------
In synaptic search for linux-image to choose to delete old ones
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

A Very Easy Alternate GUI Method - Ubuntu-Tweak
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

How to: Create a Customized GRUB2 Screen that is Maintenance Free. 
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

