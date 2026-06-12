---
title: "Problems installing via Debian"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by urbanmojo on 2007-11-15
Hi:

I don't have a CD Rom and am trying to install via this doc:

[https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies)

I have had a few problems here:
1. I couldn't partition as described during the "expert" install, that option wasn't available.
2. I did a regular Debian install (meaning it would install Debian all the way, and then tried the following steps:

mkdir work 
cd work
wget [http://ftp.bit.nl/ubuntu/pool/main/d/debootstrap/debootstrap_0.2.45ubuntu36_i386.deb](http://ftp.bit.nl/ubuntu/pool/main/d/debootstrap/debootstrap_0.2.45ubuntu36_i386.deb)
(a full list of ARCHIVE mirrors is available at: [http://ubuntulinux.org/wiki/Archive](http://ubuntulinux.org/wiki/Archive)). 
ar -x debootstrap_0.2.45ubuntu36_i386.deb
cd /
zcat < /work/data.tar.gz | tar xv
/usr/sbin/debootstrap --arch i386 hoary /target [http://ftp.bit.nl/ubuntu/](http://ftp.bit.nl/ubuntu/)

I downloaded instead the most recent distribution ...0.3.3.0_ubuntu7_all.deb (is that the one I should be getting?), but then if I tried to run the "ar" command it gives me "bad command".

My main question for now is, why isn't the "ar" command working?

Thanks!

---

