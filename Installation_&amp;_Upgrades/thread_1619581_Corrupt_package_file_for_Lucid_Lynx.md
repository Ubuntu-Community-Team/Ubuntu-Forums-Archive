---
title: "Corrupt package file for Lucid Lynx?"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by kpbenz on 2010-11-12
Hi,

I tried to update my current 10.04 release and I currently always get complaints from BZIP2 about a potentially corrupt Package file.  So I downloaded it separately with wget and tested it with bzip2:

```

# wget http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2
# bzip2 -t Packages.bz2
Packages.bz2: data integrity (CRC) error in data

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

```

I tried different servers and found the same problem on these, too. 

Can someone verify this?

Is there anything I can do about this?

TNX!

---

### Post by lemming465 on 2010-11-13
It's working OK for me from Madison, WI, US on 11/13/2010.

---

### Post by kpbenz on 2010-11-15
Thank you for checking, that eliminates one source of errors :-)

The remaining suspects are: my internet provider (which is new), my DSL modem (also new) or my laptop (old).

---

### Post by lemming465 on 2010-11-16
You could try lowering your MTU (e.g. ip link set eth0 mtu 1280) and see if that makes any difference.  1280 happens to be the IPv6 minimum, but for IPv4 it's small enough that it should survive most tunnel scenarios, if the ISP is incurring any behind your back.

---

