---
title: "Daily i386 kernel PPA disappeared?"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by Embedded Linux Guy on 2011-05-03
Hi, I have been downloading daily i386 kernel .debs from

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/current/")

However today I see there are only amd64 builds here. Not long ago I could get _i386.deb packages, but now they are all _amd64.deb. Can someone please point me to where I can get fresh kernels? Thanks!

---

### Post by Embedded Linux Guy on 2011-05-04
To (partially) answer my own question, it appears to me that the daily build has just been broken for i386 since 20 April when the build host/target apparently changed from Natty to Oneiric. Possibly I should file a bug on Launchpad.

19 April 2011: OK
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/BUILD.LOG](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/BUILD.LOG)

20 April 2011: FAIL
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-oneiric/BUILD.LOG](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-oneiric/BUILD.LOG)

---

### Post by derfan on 2012-09-26
Hi,

does this kernel in this ppa really still support i386 Architechture? I have some alix boards with the AMD Geode LX processor and I would LOVE to see precise running on them but since 12.04 it didnt seem possible any more due to the lack of the kernel's i386 support?

Thank you!
Benjamin

---

