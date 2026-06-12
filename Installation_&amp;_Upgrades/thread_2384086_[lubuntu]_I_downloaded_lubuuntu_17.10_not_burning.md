---
title: "[lubuntu] I downloaded lubuuntu 17.10 not burning"
date: 2018-02-02
forum: Installation &amp; Upgrades
---

### Post by hitsos on 2018-02-02
I downloaded lubuntu17.10 and I tried burning it to a usb using YUMI and it pops a message that it cannot open it as a archive

[http://releases.ubuntu.com/17.10/ubuntu-17.10.1-desktop-amd64.iso.torrent](http://releases.ubuntu.com/17.10/ubuntu-17.10.1-desktop-amd64.iso.torrent)

---

### Post by TheFu on 2018-02-02
Welcome to the forums.  A .torrent file isn't what you need. A bittorrent client will download the full .iso file, which should be validated using an md5sum or sha256sum program to ensure it is perfect BEFORE using any tool to copy the .iso onto a flash drive.  

A tutorial: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows)

But I could have misunderstood the issue.

---

### Post by hitsos on 2018-02-02
*thank you forgot to md5* 

there is no md5 code thought
the issue might be by ubuntu thought

how to contact ubuntu?

---

### Post by TheFu on 2018-02-02
> **hitsos said:**
> *thank you forgot to md5* 

there is no md5 code thought
the issue might be by ubuntu thought

how to contact ubuntu?

I don't understand the question.  I'm positive your English is better than my attempt in your language, just some of the words don't seem correct. Can you try the question again, please?

Ubuntu is just a distro. If you seek formal support, then you need a support contract from Canonical. They don't really do that for non-corporate clients.  You can try calling the Canonical office in your country or region.

MD5 isn't as unique as we used to think. Best to use sha256sum.  
Which flavor of Ubuntu 17.10.1 did you get?  The sha256sums are listed.
```
1a3d2d32ada795e5df47293745a7479bcb3e4e29d8ee1eaa114350b691cf38d3 *ubuntu-17.10.1-desktop-amd64.iso
8ff73f1b622276758475c3bd5190b382774626de5a82c50930519381f6c3a3f8 *ubuntu-17.10.1-server-amd64.iso
eb921425349d2a51f90edc3977f83fb6fd8aed082b31515f1bde00d46b260492 *ubuntu-17.10.1-server-i386.iso

```
Lubuntu, Xubuntu, Ubuntu-mate, Ubuntu-Bungie .... would have different sums.

You should check the sums yourself from reputable, gpg-signed, sources.  I wouldn't trust anything posted by "some guy over the internet" in a forum.  Heck, I barely trust myself. ;)

BTW, running 17.10.1 might not be the best idea for someone new to Linux. Noobs should probably use a Long Term Support release, which 16.04.3 is the current version. [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

 Non-LTS releases only have 9 months of patches. Whereas LTS releases have 5 years of patches provided you patch every few weeks to stay on supported kernels and releases the entire time.  [https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life) has a chart with release support.  Be certain to scroll half-way down to see the unexpected kernel upgrade requirements to keep support that many people miss.

---

### Post by vasa1 on 2018-02-02
Moved here for a better fit.

---

### Post by oldos2er on 2018-02-03
> **hitsos said:**
> *thank you forgot to md5* 

there is no md5 code thought


Sure there is, links here: [http://releases.ubuntu.com/artful/](http://releases.ubuntu.com/artful/)

---

