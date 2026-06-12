---
title: "pk-client-error-quark: Cannot download packages whilst offline (257)"
date: 2021-06-10
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2021-06-10
I installed Ubuntu 20.04.2 LTS server and later upgraded to desktop. I'm using netplan with networkd as the renderer and upgrades, installs, etc via the command line work without a problem.

If I use the software updater app, I get the this error

```
pk-client-error-quark: Cannot download packages whilst offline (257)
```

The network is up, so not sure why I get this.

---

### Post by MAFoElffen on 2021-06-11
Can you post your netplan config from /etc/netplan/*.yaml?

---

### Post by lister171254 on 2021-06-12
I followed the instruction on how to disable network manager
[https://www.configserverfirewall.com/ubuntu-linux/ubuntu-network-manager/](https://www.configserverfirewall.com/ubuntu-linux/ubuntu-network-manager/)

and everything now works as expected.

---

### Post by MAFoElffen on 2021-06-12
Good job, and good luck.

---

