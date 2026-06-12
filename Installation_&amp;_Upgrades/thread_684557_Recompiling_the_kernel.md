---
title: "Recompiling the kernel"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by Mithrilhall on 2008-02-01
I've downloaded the linux-2.6.23.12 kernel and patched it and iptables-1.4.0 with patch-o-matic-ng-20071226.
```

lrwxrwxrwx  iptables -> iptables-1.4.0
drwxr-xr-x  iptables-1.4.0
-rw-r--r--  iptables-1.4.0.tar.bz2
drwxr-xr-x  l7-protocols-2007-11-22
-rw-r--r--  l7-protocols-2007-11-22.tar.gz
lrwxrwxrwx  linux -> linux-2.6.23.12
drwxrwxr-x  linux-2.6.23.12
lrwxrwxrwx  linux-2.6.23.12-slh-smp-2 -> linux-headers-2.6.23.12-slh-smp-2
-rw-r--r--  linux-2.6.23.12.tar.bz2
-rw-r--r--  linux-custom-patches-2.6.23.12-slh-smp-2.tar.bz2
drwxr-xr-x  linux-headers-2.6.23.12-slh-smp-2
-rwxr-xr-x  linux-source-2.6.23.12-slh-smp-2.sh
drwxr-xr-x  netfilter-layer7-v2.17
-rw-r--r--  netfilter-layer7-v2.17.tar.gz
drwxr-xr-x  patch-o-matic-ng-20071226
-rw-r--r--  patch-o-matic-ng-20071226.tar.bz2

```
When I try compiling the kernel this is where it dies.
```

root@siduxbox:/usr/src# make-kpkg --initrd --append-to-version=-ms.01 kernel_image kernel_headers
.......
CC [M]  net/ipv4/netfilter/ipt_connlimit.o
net/ipv4/netfilter/ipt_connlimit.c: In function 'count_them':
net/ipv4/netfilter/ipt_connlimit.c:98: error: too many arguments to function 'nf_conntrack_find_get'
net/ipv4/netfilter/ipt_connlimit.c: At top level:
net/ipv4/netfilter/ipt_connlimit.c:312: warning: initialization from incompatible pointer type
net/ipv4/netfilter/ipt_connlimit.c:316: warning: initialization from incompatible pointer type
make[4]: *** [net/ipv4/netfilter/ipt_connlimit.o] Error 1
make[3]: *** [net/ipv4/netfilter] Error 2
make[2]: *** [net/ipv4] Error 2
make[1]: *** [net] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.23.12'
make: *** [debian/stamp-build-kernel] Error 2
root@siduxbox:/usr/src/linux# 

```

---

