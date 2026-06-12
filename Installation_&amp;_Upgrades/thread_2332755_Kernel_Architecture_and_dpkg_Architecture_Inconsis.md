---
title: "Kernel Architecture and dpkg Architecture Inconsistency - How to Fix?"
date: 2016-08-03
forum: Installation &amp; Upgrades
---

### Post by SAH62 on 2016-08-03
I'm working with a Linode VM that was originally set up with a 32-bit kernel and Ubuntu 14.04 LTS. At some point I used Linode's management interface to upgrade to a 64-bit kernel. "uname -a" returns this information:

```

$ uname -a
Linux <node name> 4.5.5-x86_64-linode69 #3 SMP Fri May 20 15:25:13 EDT 2016 x86_64 x86_64 x86_64 GNU/Linux
$

```

I recently found that the dpkg build and host architectures on my VM are still 32-bit "i386":

```

$ dpkg-architecture
DEB_BUILD_ARCH=i386
DEB_BUILD_ARCH_BITS=32
DEB_BUILD_ARCH_CPU=i386
DEB_BUILD_ARCH_ENDIAN=little
DEB_BUILD_ARCH_OS=linux
DEB_BUILD_GNU_CPU=i686
DEB_BUILD_GNU_SYSTEM=linux-gnu
DEB_BUILD_GNU_TYPE=i686-linux-gnu
DEB_BUILD_MULTIARCH=i386-linux-gnu
DEB_HOST_ARCH=i386
DEB_HOST_ARCH_BITS=32
DEB_HOST_ARCH_CPU=i386
DEB_HOST_ARCH_ENDIAN=little
DEB_HOST_ARCH_OS=linux
DEB_HOST_GNU_CPU=i686
DEB_HOST_GNU_SYSTEM=linux-gnu
DEB_HOST_GNU_TYPE=i686-linux-gnu
DEB_HOST_MULTIARCH=i386-linux-gnu
$


```

Is there any way I can update/upgrade aptitude and dpkg for the 64-bit amd64 architecture? Would an OS upgrade from 14.04.4 LTS to 16.04.1 LTS get me there?

---

### Post by papibe on 2016-08-03
Hi SAH62.

It can be done, however...

It is something that there's no standard procedure and tools to achieve it. It would much easier to reinstall.

Nevertheless, here's a guide for advance sys-admins: [Upgrading Debian From i386 To amd64]("http://users.digitalkingdom.org/~rlpowell/hobbies/debian_arch_up/index.html").

Again, if I were you, I'd just reinstall.

Best Regards.

---

### Post by SAH62 on 2016-08-05
Thanks, papibe. Since a failed crossgrade would require reinstalling anyway, I decided to give it a try - and I managed to make it work. It wasn't easy and there were more than a few things that needed to be fixed along the way, but all seems well and I'm now ready for the upgrade to 16.04.1.

---

