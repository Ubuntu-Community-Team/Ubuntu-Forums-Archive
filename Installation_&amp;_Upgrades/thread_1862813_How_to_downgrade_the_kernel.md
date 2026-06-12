---
title: "How to downgrade the kernel?"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by geronimo66 on 2011-10-17
Hello,

since the issue I'm having with the unsupported control of the fan of the Toshiba Satellite seems to be unsolvable, the only way remaining is the downgrading of the kernel.
( [http://ubuntuforums.org/showthread.php?p=11351871](http://ubuntuforums.org/showthread.php?p=11351871) ).
Is here someone to tell
1) where I may get an ubuntu-kernel of maybe 2.6.32 or lower?
2) are there any serious obstacles to set an old kernel up within a newer distribution (I'm running natty) fully functional?

thanx for helping

geronimo

---

### Post by dino99 on 2011-10-17
sudo apt-get install toshset

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

chosse an empty folder to download your kernel (2 headers + 1 image)
cd to that folder, then: sudo dpkg -i *.deb

---

