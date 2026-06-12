---
title: "Debootstrap 1.0.37 missing apt-get"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by ijh36527 on 2011-12-01
I'm trying to use deboostrap 1.0.37 on Ubuntu 11.10 to setup a rootfs for Scratchbox 2. Debootstrap does not include apt-get with an armel debian rootfs though, making it difficult to install extra packages. This seems to have been a bug in version 1.0.20 but was fixed, see [https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/533369](https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/533369). Any suggestions? 

I'm using the following command:

sudo debootstrap --verbose --arch armel --foreign --variant=scratchbox squeeze Code/sbox2/rootfs/squeeze [http://ftp.at.debian.org/debian](http://ftp.at.debian.org/debian)

Thanks,
Ira

---

