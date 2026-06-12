---
title: "Updating kernel from generic to i386"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by MaestroS on 2007-05-18
I want to know, where I can download this:
linux-386 linux-image-386 linux-restricted-modules-386

and how do I update my current kernel (ubuntu 7.04; generic) to i386 ?

---

### Post by Soybean on 2007-05-18
They're all available in Synaptic. Or use aptitude:
```
sudo aptitude install linux-386 linux-image-386 linux-restricted-modules-386
```
You may have to fiddle around with /boot/grub/menu.lst to get it to be the default kernel.

Before you start, though... why do you want to? I'm not aware of any benefits.

---

### Post by MaestroS on 2007-05-18
I've got wireless internet with Wireless rt2400 card, so I need to change kernel into i386 from current - generic : /

PS: I can't get anything from repos.
I don't have internet connection yet - that's why I need new kernel.

---

### Post by Soybean on 2007-05-18
Hmm. It ought to be possible to get the rt2400 drivers working with the generic kernel, too... Have you looked at this page: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82711](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82711)? It sounds like some of those people got similar problems sorted out. Something about an incompatibility between network manager and the rt2400 drivers.

For the issue where you can't get the repositories because your network doesn't work -- there's a way to get aptitude or synaptic to use a Ubuntu CD as a repository if your network isn't working. I've never done it, but I think it may be as easy as sticking the CD in the drive and trying again... if not, hopefully someone else will chime in with a proper explanation.

---

### Post by mikewhatever on 2007-05-18
> **MaestroS said:**
> I've got wireless internet with Wireless rt2400 card, so I need to change kernel into i386 from current - generic : /

PS: I can't get anything from repos.
I don't have internet connection yet - that's why I need new kernel.

Here you go [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=2.6.20-15-386&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=2.6.20-15-386&searchon=names&subword=1&version=feisty&release=all)

---

