---
title: "update of linux-ubuntu-modules breaks linux-rt"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by 1ino1eum on 2007-12-16
Hello, 
I m with gusty and I have previously installed :

linux-restricted-modules-2.6.22-14-rt (2.6.22.4-14.10)
linux-restricted-modules-rt (2.6.22.14.21)
linux-rt (2.6.22.14.21)



the 12/12/2007, this packages have been updated :

linux-ubuntu-modules-2.6.22-14-generic (2.6.22-14.37) to 2.6.22-14.38
linux-ubuntu-modules-2.6.22-14-rt (2.6.22-14.37) to 2.6.22-14.38

since then, I've got an error (video drivers not detected/dont work) at the boot, and I have the configuration window.

I've got an nvidia 8800gtx, everything run perfectly with the generic kernel.

---

### Post by Trackieman on 2007-12-16
Sounds like X is trying to possibly use the proprietary nvidia driver that you had as a module with your previous kernel?

---

### Post by 1ino1eum on 2007-12-19
so, any help, or advice on what I should do or try?
otherwise the only option for me is to reinstall ubuntu with ubuntustudio this time ... :/
but reinstalling evertyhing is an hassle...

---

### Post by Elaztic on 2007-12-19
I have the exact same problem.
Anyone found a solution??

Update:
So glad we have such intelligent people in this forum (thx Rexxxlo).
The solution is in this thread: [http://ubuntuforums.org/showthread.php?t=642221](http://ubuntuforums.org/showthread.php?t=642221)
The short version:
> sudo dpkg-reconfigure xserver-xorg 

---

