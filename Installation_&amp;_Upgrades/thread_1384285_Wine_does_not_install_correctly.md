---
title: "Wine does not install correctly"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by valexi on 2010-01-18
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up wine (1.0.1-0ubuntu8) ...
kernel.printk = 4 4 1 7
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.tcp_syncookies = 1
vm.mmap_min_addr = 0
error: "Invalid argument" setting key "kernel.shmall"
dpkg: error processing wine (--configure):
 subprocess installed post-installation script returned error exit status 255
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 wine
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

After installing I can see the Wine drop-down menu under the Applications, but every time I install something, updates etc.  I can see this same error. How can this be fixed?

---

### Post by x33a on 2010-01-18
take a look here:

[https://bugs.launchpad.net/ubuntu/+source/procps/+bug/461489](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/461489)

---

### Post by valexi on 2010-01-18
That fixed it for me!

Thanks!

---

