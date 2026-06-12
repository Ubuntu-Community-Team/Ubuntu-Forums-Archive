---
title: "Problems during the update process of some packages"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by jisaac on 2007-01-10
Hello,

I was updating some packages yesterday as I do usually with the "Software Updates" of Edgy but this time I had a problem. I get few packages broken. I used the "broken" filter in the "Synaptic Package Manager" to solve the problem.

But now I have 2 packages "libc6" and "libc6-i686" that I'm not able to update. Hereunder I pasted the error message:

----------
(Reading database ... 105280 files and directories currently installed.)
Preparing to replace libc6 2.4-1ubuntu12 (using .../libc6_2.4-1ubuntu12.1_i386.deb) ...
Matching libraries: /usr/lib/libpthread.so.20 /lib/ld-linux.so.2

A copy of glibc was found in an unexpected directory.
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library and try again.
dpkg: error processing /var/cache/apt/archives/libc6_2.4-1ubuntu12.1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.4-1ubuntu12.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
----------

-> Where is the "glibc" I have to remove before upgrading? I'm afraid to do something like this...

-> The update (yesterday) included the "xserver"... I can not install again my nvidia drivers because of an error due to the "glibc" package.

Any help?

Thanks.

---

### Post by arnieboy on 2007-01-10
> **jisaac said:**
> Hello,

I was updating some packages yesterday as I do usually with the "Software Updates" of Edgy but this time I had a problem. I get few packages broken. I used the "broken" filter in the "Synaptic Package Manager" to solve the problem.

But now I have 2 packages "libc6" and "libc6-i686" that I'm not able to update. Hereunder I pasted the error message:

----------
(Reading database ... 105280 files and directories currently installed.)
Preparing to replace libc6 2.4-1ubuntu12 (using .../libc6_2.4-1ubuntu12.1_i386.deb) ...
Matching libraries: /usr/lib/libpthread.so.20 /lib/ld-linux.so.2

A copy of glibc was found in an unexpected directory.
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library and try again.
dpkg: error processing /var/cache/apt/archives/libc6_2.4-1ubuntu12.1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.4-1ubuntu12.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
----------

-> Where is the "glibc" I have to remove before upgrading? I'm afraid to do something like this...

-> The update (yesterday) included the "xserver"... I can not install again my nvidia drivers because of an error due to the "glibc" package.

Any help?

Thanks.
paste the result of the following:
```
cat /etc/apt/sources.list
```

---

### Post by jisaac on 2007-01-13
I found the solution there:

[http://shearer.org/Debugging_Dpkg_Problems](http://shearer.org/Debugging_Dpkg_Problems)

Everything is working fine now!

---

