---
title: "After Update from 9.04 to 10.04: LUKS-Encrypted USB Disks and USB Surfstick dont work"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by kindergartencop on 2010-07-02
Hello all,

I have problems with functionality that was already there in 9.04 and became inaccessible for me after upgrading to 10.04.

Luks-encrypted partitions on USB disks are no longer recognized by the system as they have been and I keep having to mount them manually. Previously they were automatically detected and even mounted if a key was found in the keyring.

Also, Network-Manager keeps ignoring my Huawei E160 surf stick even though this is a pretty common model and worked like a charm in NM before the upgrade. The stick is properly initialized by the kernel and I can manually access it via ttyUSB0 or use it via wvdial. However, using it with network-manager was so much more convenient and I just wonder why it keeps getting ignored.

I already filed bugs on launchpad for both of the issues, however that was almost a month ago and noone seems to bother making at least suggestions or asking for more info.

Maybe someone here can give me hints on where to look for the problems so that I can make some of my most-used features work well again.

Thank you!

---

### Post by davidmohammed on 2010-07-02
... [this guy]("http://ubuntuforums.org/showthread.php?t=1473228&page=2") says he as solved the issue with you 160 stick...

can you try his suggestion?

---

### Post by kindergartencop on 2010-07-03
> **davidmohammed said:**
> ... [this guy]("http://ubuntuforums.org/showthread.php?t=1473228&page=2") says he as solved the issue with you 160 stick...

can you try his suggestion?

Thank you. Of course I have already done searches for the problem before I posted my bugs and this thread, and found similar solution HowTos. In fact, it is not the problem to have my GSM modem being recognized by the kernel but it is that Network-Manager does not get to know about the presence of the modem that it normally would support. 

The modechange fix that your link is pointing to is already installed on my system and working - otherwise I would not be able to use the surf stick at all. I am just searching fo a way to make the stick known to Network-Manager, so that I do not need to use other dialin software for it.

---

### Post by davidmohammed on 2010-07-03
does wicd work for you or does it have the same issue as network manager?

---

### Post by kindergartencop on 2010-07-04
> **davidmohammed said:**
> does wicd work for you or does it have the same issue as network manager?

As far as I know, support for 3G USB modems aint yet implementet in wicd at all, but is planned for the next major release (v2).

My guess is that NM is being told about new devices using some system messaging service but that this service doesnt work properly and needs to be told that it has to inform NM about this specific device.
Unfortunately thats about how deeply I know about that system internal messaging stuff and I was hoping that someone else might be able to shift me a little bit further down the path. Like telling me "you need to debug this by using program xy then you can see whats going wrong".

---

