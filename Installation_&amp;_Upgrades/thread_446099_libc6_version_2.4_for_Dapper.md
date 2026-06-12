---
title: "libc6 version 2.4 for Dapper"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by jefferbean on 2007-05-16
I've successfully installed the Sun Java Wireless Toolkit 2.5.1 on my laptop, but when I attempt to build/run a project, I get the following error:

/lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found

Apparently I need version 2.4 of libc6, but according to Synaptic I currently have the 2.3.6-0ubuntu20.4 version installed.  Is it possible to get version 2.4 in Dapper (6.06), or must I upgrade my distro to Edgy or Feisty??  I know that sometimes it's possible to edit sources.list with repositories for newer distro, and then just install the newer libc6 package, but I'm worried this might break a bunch of other Dapper packages dependent on the older libc6.

(I was hoping to wait on upgrading to Feisty, because I'm using this machine to develop for a project that's due in a week, and I'd rather not risk breaking everything that works already)

Any help is greatly appreciated.  Thanks!

---

### Post by eternauta3k on 2007-06-08
Having the same problem, I'd rather not upgrade to a newer ubuntu right now.

---

### Post by az on 2007-06-08
Any way you can compile it from source?  It seems that the version you are using is not binary-compatible.  Compiling from source would make it binary compatible (by definition)

---

### Post by primo on 2007-10-26
I had the same problem myself. I was able to get it working with only three packages from the edgy repository:

[linux-libc-dev (2.6.17.1-12.41)](http://packages.ubuntu.com/edgy/devel/linux-libc-dev)
[libc6-dev (2.4-1ubuntu12)](http://packages.ubuntu.com/edgy/libdevel/libc6-dev)
[libc6 (2.4-1ubuntu12)](http://packages.ubuntu.com/edgy/base/libc6)

Before you can install linux-libc-dev, you will need to remove linux-kernel-headers (it seems to be a direct replacement). Also, installing libc6 removed a lot of packages, including g++, libsdl1.2-dev, and zlib1g-dev, to name a few. However, I assume this was because I installed the packages in the opposite order that I've listed them here, and worked my way back up the dependency tree. After I had installed all three, I was able to reinstall all of the removed packages.

---

