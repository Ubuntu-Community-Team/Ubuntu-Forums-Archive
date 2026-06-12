---
title: "libsgutils2-1.46-2_1.46-3ubuntu2_amd64.deb dpkg error."
date: 2023-11-21
forum: Installation &amp; Upgrades
---

### Post by rnnscientist on 2023-11-21
Upgrading from lunar to Mantic, cannot install any apt packages because ```
**Sub-process /usr/bin/dpkg returned an error code (1)**
```

This is the whole error when i try to install any package: 
```
dpkg: error processing archive /var/cache/apt/archives/libsgutils2-1.46-2_1.46-3ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libsgutils2-1.46.so.2.0.0', which is also in package libsgutils2-2:amd64 1.46-1ubuntu0.
23.04.1
Errors were encountered while processing:
 /var/cache/apt/archives/libsgutils2-1.46-2_1.46-3ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Tried:
1.  Running ```
sudo dpkg --configure -a
```
 Error: 
```
dpkg: dependency problems prevent configuration of libgpod-common:
 libgpod-common depends on libsgutils2-1.46-2 (>= 1.27); however:
  Package libsgutils2-1.46-2:amd64 is not installed.

dpkg: error processing package libgpod-common (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.38-1ubuntu6) ...
Errors were encountered while processing:
 libgpod-common

```

---

### Post by MAFoElffen on 2023-11-21
Please visit this, and select the link in the upper right as "affects you"... Bug Report: [https://bugs.launchpad.net/ubuntu/mantic/+source/sg3-utils/+bug/2039279](https://bugs.launchpad.net/ubuntu/mantic/+source/sg3-utils/+bug/2039279)

Also:
[https://bugs.launchpad.net/ubuntu/+source/sg3-utils/+bug/2043977](https://bugs.launchpad.net/ubuntu/+source/sg3-utils/+bug/2043977)
[https://bugs.launchpad.net/ubuntu/+source/sg3-utils/+bug/2039348](https://bugs.launchpad.net/ubuntu/+source/sg3-utils/+bug/2039348)

---

