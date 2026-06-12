---
title: "Are the repos for Lucid gone?"
date: 2017-06-17
forum: Installation &amp; Upgrades
---

### Post by bambib on 2017-06-17
I'm trying to install Lucid (more recent versions of Linuxcnc aren't working, so I'm trying to revert to what DID work) but I'm getting lots of missing repo errors.

Are they REALLY missing?  Or have they maybe been moved?


```
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  404  Not Found [IP: 2001:67c:1562::16 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Michael Dooley on 2017-06-17
Not exactly gone, but located somewhere else. I think what you're looking for can be found here -

[http://old-releases.ubuntu.com/ubuntu/dists/lucid/](http://old-releases.ubuntu.com/ubuntu/dists/lucid/)

If not, then google ubuntu old packages.

---

### Post by oldos2er on 2017-06-17
Lucid has long since reached its end-of-life, and is not safe to run. Please install a supported version of Ubuntu, 14.04 LTS, 16.04 LTS, or 17.04. If you're looking for something lighter for older hardware, try [Lubuntu]("http://lubuntu.me/").

---

### Post by Bucky Ball on 2017-06-17
Welcome. Lubuntu if you are having trouble getting newer Ubuntu to run, as mentioned by oldos2er, and I'd also suggest giving Xubuntu a try. Avoid EOL releases.

Presume this is an older machine with low RAM and hardware? If a modern machine with plenty of RAM, we may be able to get to the bottom of why you can't install Ubuntu.

---

### Post by mörgæs on 2017-06-18
The problem is not hardware but that LinuxCNC is not released for present Buntu versions. 

I have seen the problem before but can't provide an easy solution. The discussion [here]("https://forum.linuxcnc.org/9-installing-linuxcnc/31910-ubuntu-16-04-x64-and-linuxcnc-2-8-0-2-7-7") suggests that Debian Wheezy might work better though not perfect. Installing in Buntu 16.04 seems a complicated process.

---

### Post by Bucky Ball on 2017-06-18
Thanks for pointing out, morgaes. The user hainjedaf has Linuxcnc running on Ubuntu 16.04 and [gives full instructions for how to do it here]("https://forum.linuxcnc.org/9-installing-linuxcnc/31910-ubuntu-16-04-x64-and-linuxcnc-2-8-0-2-7-7#83581") (read last post), but you're right; looks pretty involved.

---

