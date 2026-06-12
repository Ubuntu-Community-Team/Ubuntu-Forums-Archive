---
title: "Having issue installing setools on Ubuntu 14.04"
date: 2015-09-09
forum: Installation &amp; Upgrades
---

### Post by Majortom71 on 2015-09-09
Hello,

I am trying to build setools from source and I have encountered the following error during build.

libqpol/policy_extend.c:42:29: fatal error: selinux/selinux.h: No such file or directory
 #include <selinux/selinux.h>

I check the /usr/include folder and the selinux/ folder does not exist.
I have searched regarding this issue and people have mentioned that you need to obtain the kernel headers to address this.

I checked /usr/src and it does contain the headers:
[COLOR=#0000ff]linux-headers-3.13.0-44          linux-headers-3.13.0-45          linux-headers-3.13.0-46          linux-headers-3.13.0-49          linux-headers-3.13.0-51          nvidia-304-304.125  virtualbox-guest-4.3.10[/COLOR]
[COLOR=#0000ff]linux-headers-3.13.0-44-generic  linux-headers-3.13.0-45-generic  linux-headers-3.13.0-46-generic  linux-headers-3.13.0-49-generic  linux-headers-3.13.0-51-generic  vboxhost-4.3.30     volatility-tools[/COLOR]



At this point I am not sure what else needs to be done.

Can anyone help guide me on this issue.

Thank you.

P.S. It looks like I accidentally posted in the wrong area.  If an admin can move this I appreciate it.

---

### Post by Toz on 2015-09-10
You can use "apt-file" to find which packages missing files are located in or use the [online package search]("http://packages.ubuntu.com/").

The package that you need to install is **libselinux1-dev**.
```
$ apt-file search selinux.h | grep "/usr/include/"
libselinux1-dev: /usr/include/selinux/selinux.h
```

---

