---
title: "Ubuntu vmware install"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by dataforcecrm on 2007-07-20
where are the linux kernel source stored in the file tree please?

---

### Post by dabl on 2007-07-20
Open your System>Administration>Synaptic package manager, and scroll down to the "linux-xxx" packages.  Make sure the source you select matches the kernel you have.  ```
uname -a
``` will tell you what you have.

---

### Post by scxtt on 2007-07-20
**/usr/src/linux** should be symbolically linked to whatever kernel source you're compiling for ...
```
:> ll /usr/src
total 4.0K
lrwxrwxrwx  1 root root   22 May 30 01:55 linux -> linux-2.6.20-gentoo-r8
drwxr-xr-x 20 root root 4.0K Jun 19 05:03 linux-2.6.20-gentoo-r8
```

---

