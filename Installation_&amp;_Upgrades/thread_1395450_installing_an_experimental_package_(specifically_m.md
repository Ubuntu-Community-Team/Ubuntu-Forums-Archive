---
title: "installing an experimental package (specifically mdadm 3.1.1) ?"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by ljwobker on 2010-01-31
I've been doing a lot of mdadm/raid testing, and I see that the next step is to upgrade the version of mdadm that I'm using.  On my Karmic 9.10 build the default package is:

root@lwobker-ubuntu:/dev# mdadm --version
mdadm - v2.6.7.1 - 15th October 2008

according to the mdadm maintainers, 3.1.1 is out and considered stable enough for testing... so my question is... how do I install the package with the new version? 

I can see the source code here, but I would much much rather install a package (which has been built at least for debian -- are they one and the same for ubuntu?

[http://www.kernel.org/pub/linux/utils/raid/mdadm/](http://www.kernel.org/pub/linux/utils/raid/mdadm/)
[http://packages.debian.org/experimental/mdadm](http://packages.debian.org/experimental/mdadm)

thanks for walking a partial noob through this.

---

### Post by falconindy on 2010-02-01
o hai. The debian.org page you provided gives links for .deb files at the bottom. Click on your architecture and then your choice of mirror.

It may not be identical to an Ubuntu package, but it may be close enough. MDADM is fairly low level.

edit: insanely low level, it turns out. It only depends on 1 shared library (libc6) which has a stricter requirement in Ubuntu than Debian's experimental package. I'd be surprised if you couldn't get this installed.

---

### Post by ljwobker on 2010-02-01
OK... so I managed to get this to work by downloading the actual .deb file and then running 
```
dpkg -i <whatever.deb>
```
I was sort of hoping I could do this via the normal apt-get or synaptic package installer... is that an easy thing to describe to a package-noob like me?

---

### Post by falconindy on 2010-02-01
aptitude, apt-get and synaptic can be thought of as fancy front ends for dpkg. In the end, they all result in your package database being updated and the program being installed. You can easily do "sudo apt-get remove mdadm" and it'll remove this newly installed package.

---

### Post by tgrimley on 2010-02-09
You have any luck getting 3.1.1 to work?  What version of ubuntu are you running?  I'm looking to level migrate my raid5 to raid6 :)

---

