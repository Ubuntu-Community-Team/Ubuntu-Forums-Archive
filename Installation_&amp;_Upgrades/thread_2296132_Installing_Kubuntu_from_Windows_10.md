---
title: "Installing Kubuntu from Windows 10"
date: 2015-09-23
forum: Installation &amp; Upgrades
---

### Post by Daniel_OC on 2015-09-23
Hello guys, I realised my USB drive doesn't work anymore and I got the Live CD I downloaded from the website.

Unfortunately I can't install it without it so I was wondering if it is possible to install it from Windows 10. I read about wubi but everytime I use it the thing will just say I don't have permissions or freeze (or redownload de ISO which I already have since I open it from inside the directory).

Is there any way I can do this? 

I have the partition and everything ready!

---

### Post by grahammechanical on 2015-09-23
Wubi is not longer being developed. It was not compatible with Windows 8. So, I doubt if it is compatible with Windows 10. The position of the fourm on wubi is staed here

[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

Regards.

---

### Post by yancek on 2015-09-23
> Unfortunately I can't install it without it so I was wondering if it is possible to install it from Windows 10.

Simple answer, no.  The wubi method no longer developed/supported doesn't work on iwndows 8 or later as pointed out above and a default windows install isn't even able to read a Linux filesystem much less write to it.  Years ago, there was a somewhat convoluted method using xp wherein you copied certain parts of the partition with boot code to a file in windows and put it in a specified location and then manually configured a boot entry with the boot file.  I imagine something similar could be done with newer windows but you would need a lot of knowledge on the windows boot process.  On the other hand, windows may have changed the boot process so that something like this won't work.

---

