---
title: "Libc6, libc6-dev, libstdc++6-4.1-dev"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by jordxn on 2010-02-04
I have a fairly old Debian server that I'm trying to update some packages on - however, I'm having the exact same problem as on this form (archive);
[http://ubuntuforums.org/showthread.php?t=344570&page=4](http://ubuntuforums.org/showthread.php?t=344570&page=4)

ie. "A copy of glibc was found in an unexpected directory"

So how do I solve this problem? On the bug report;
[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/81125](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/81125)
it says "Simply wait for the next update to be available from your local mirror, and install it when it arrives." 

I tried to just update the lib like;

```
apt-get install libc6
```
but I get
```
Matching libraries: /usr/lib/libc.so.6

A copy of glibc was found in an unexpected directory.
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library and try again.
dpkg: error processing /var/cache/apt/archives/libc6_2.7-18lenny1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.7-18lenny1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

My APT Sources;
```

deb http://debian.yorku.ca/debian/ stable main non-free contrib
deb-src http://debian.yorku.ca/debian/ stable main non-free contrib
deb http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
deb-src http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free

```

Thanks for any help!!
Jordan

---

