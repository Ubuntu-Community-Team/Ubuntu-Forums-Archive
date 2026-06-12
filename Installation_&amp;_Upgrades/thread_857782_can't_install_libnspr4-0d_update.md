---
title: "can't install libnspr4-0d update"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by Straumoy on 2008-07-12
Hello,

I have issues installing this update. It downloads just fine, but when it comes to the installation, I get the following error message:

E: /var/cache/apt/archives/libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.3_i386.deb: trying to overwrite `/usr/lib/libnspr4.so', which is also in package libnspr4

the terminal window gives further details:

(Reading database ... 180288 files and directories currently installed.)
Preparing to replace libnspr4-0d 4.7.1+1.9-0ubuntu0.8.04.1 (using ... /libnspr4-0d_4.7.1+1.9-0ubuntu0.8.40.3_i386.deb) ...
unpacking replacement libnspr4-0d ...
dpkg: error processing /var/cache/apt/archives/libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.3_i386.deb (--unpack):
trying to overwrite `/usr/lib/libnspr4.so`, which is also in package libnspr4
errors were encountered while processing:
/var/cache/apt/archives/libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.3_i386.deb
E: sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:



At first I thought that some files were in use and thus could not be overwritten, but I've tried to start up, then go straight to the installation of the update, but I get the same error message.

Any advice on how to solve this issue would be appreciated.

---

### Post by Partyboi2 on 2008-07-12
Looks like there has been a bug report opened, there are also a few possible workarounds mentioned. See [[COLOR=Blue]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/nspr/+bug/245122")

---

