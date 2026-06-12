---
title: "md5sum problem"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by Joe_Linux on 2006-07-25
I am not getting a matching md5sum from ubuntu-6.06-dvd-i386.iso

md5sum from the URL [http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/6.06/release/MD5SUMS](http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/6.06/release/MD5SUMS)

8a9a8e6b6a493f7b4a85cfe37872206f  ubuntu-6.06-dvd-amd64.iso
d707601cb6b006041c886d38bdf51907  ubuntu-6.06-dvd-i386.iso
6820868836d0aca20acb5c77dd0c0daf  ubuntu-6.06-dvd-powerpc.iso


The generated md5sum from the file I downloaded 

[joe@localhost ~]$ md5sum ubuntu-6.06-dvd-i386.iso
d676b514eb0c7a4d2769c59e20ca30c7  ubuntu-6.06-dvd-i386.iso
[joe@localhost ~]$
Any help would be appreciated thank you Joe_Linux

---

### Post by simonn on 2006-07-25
If the md5sums do not match, it has not been downloaded correctly.

---

