---
title: "Big problem for installing Ubuntu on Dell OPTIPLEX 790"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by bradevuu on 2011-07-05
Hi all,

Recently I got a new desktop DELL OPTIPLEX 790. According to official documentation([http://www.ubuntu.com/certification/hardware/201011-6872:201011-6873](http://www.ubuntu.com/certification/hardware/201011-6872:201011-6873)),
the only version that works for 790 is Ubuntu 11..

When I installed lower versions(such as 10.04,9.04), the screen display is totally messed up that I could not see any thing.(Ubuntu 8 works fine). I thought it might be the problem of video card.

I will do some programming job on lower versions of Ubuntu(such as 10.04).  

So any one could answer that it's the problem of hardware or incompatibility of Ubuntu for 790?  

I really appreciate your help.

---

### Post by bradevuu on 2011-07-07
no one can answer??

---

### Post by dino99 on 2011-07-07
with too recent hardware, sometimes drivers are not fully ready. So always start with the latest release (natty) and install on it the latest kernel which may have the latest chipsets modules

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

adding the latest xorg may help too:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

note: most of Dell hdds are "tatooed", have hidden partitions/files. Removing (hdd formating) them is a good idea (after backing what you want/need in case, but proprietary stuff often brings more headaches than advantages)

---

