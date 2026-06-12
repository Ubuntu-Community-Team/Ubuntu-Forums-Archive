---
title: "cannot install libc6"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by jakartographer on 2007-09-24
I'm trying to use dpkg -i to install several things, as I have no internet connection on my Kubuntu machine, and all of these things are dependant on libc6, which I have downloaded.  When I tried to install it, it tells me
```
akka@akka-desktop:~/debs$ sudo dpkg -i libc6_2.3.6-0ubuntu20_i386.deb
(Reading database ... 87167 files and directories currently installed.)
Preparing to replace libc6 2.4-1ubuntu12 (using libc6_2.3.6-0ubuntu20_i386.deb) ...
Unpacking replacement libc6 ...
Replaced by files in installed package tzdata ...
/bin/sh: /lib/libc.so.6: version `GLIBC_2.4' not found (required by /bin/sh)
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/bin/sh: /lib/libc.so.6: version `GLIBC_2.4' not found (required by /bin/sh)
dpkg: error processing libc6_2.3.6-0ubuntu20_i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
/bin/sh: /lib/libc.so.6: version `GLIBC_2.4' not found (required by /bin/sh)
dpkg: error while cleaning up:
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 libc6_2.3.6-0ubuntu20_i386.deb

```
It looks like I'm trying to replace a NEWER copy of libc6 that already exists, but that copy must not be fully installed and configured, either, since I still get dependency errors.

It turns out I have tried to install two libc6 packages, named "libc6_2.3.6-0ubuntu20_i386.deb" (the one shown above) and "libc6_2.6.1-1+b1_i386.deb", but that still leaves me with three versions of libc6, one of which I didn't know about, and two of which I'm not going to need.

Obviously, I'm really confused.  Can anyone help?  I'm not even sure what questions to ask.

---

### Post by UnixN00b on 2008-03-05
jakartographer did you get any further with this?

I am experiencing exactly the same problem.

Actually want to install libc6_2.3.6-0ubuntu20_i386.deb so I can install libsilc-1.0-2_0.9.12-4.1ubuntu2_i386.deb which depends on it so that I can install Pidgin.

Anyone got any suggestions?

Thanks.

---

### Post by zvacet on 2008-03-05
@ **jakartographer**

You are downgrading that package and I don´t understand why.If you don´t have internet download packages from other (and you are obviously doing that) comp with [nonetdebs.](http://nonetdebs.homeip.net/)That way you will download package and all dependencies.

---

