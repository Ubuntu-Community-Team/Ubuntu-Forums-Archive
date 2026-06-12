---
title: "Installed KXStudio Now Screen Is Black on Bootup"
date: 2012-03-23
forum: Installation &amp; Upgrades
---

### Post by bbarton11 on 2012-03-23
Hi All,
 
I just installed KXStudio and after all was complete, I restarted machine. After it boots the screen goes black and monitor turns itself off. I have an ATI 7500 card. Any ideas? Is GRUB jacked up?
 
Thanks,
Brian

---

### Post by oldfred on 2012-03-24
Is KXStudio Ubuntu based?

In Ubuntu it usually is graphic driver issues. Often nomodeset will get you to boot to some minimal video mode and then you may have to install video drivers.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

