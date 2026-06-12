---
title: "unmet dependencies on 12.04.2"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by cjwalther on 2013-05-07
My


```
Linux Desktop01 3.2.0-39-generic#62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 x86_64 x86_64 x86_64GNU/Linux



```has ran into:


```
dpkg: dependency problems preventconfiguration of linux-generic:
 linux-generic depends onlinux-image-generic (= 3.2.0.40.48); however:
  Version of linux-image-generic onsystem is 3.2.0.41.49.
 linux-generic depends onlinux-headers-generic (= 3.2.0.40.48); however:
  Version of linux-headers-generic onsystem is 3.2.0.41.49.

```

and I am wondering what might be the best way to fix this. I also have:

```
dpkg --list| grep linux-image
ii  linux-image-3.2.0-29-generic                     3.2.0-29.46                                   Linuxkernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-31-generic                     3.2.0-31.50                                   Linuxkernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-32-generic                     3.2.0-32.51                                   Linuxkernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-33-generic                     3.2.0-33.52                                   Linuxkernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-34-generic                     3.2.0-34.53                                   Linuxkernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-35-generic                     3.2.0-35.55                                   Linuxkernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-36-generic                     3.2.0-36.57                                   Linuxkernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-37-generic                     3.2.0-37.58                                   Linuxkernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-38-generic                     3.2.0-38.61                                   Linuxkernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-39-generic                     3.2.0-39.62                                   Linuxkernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-40-generic                     3.2.0-40.64                                   Linuxkernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-41-generic                     3.2.0-41.66                                   Linuxkernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic                              3.2.0.41.49                                   GenericLinux kernel image

```

---

### Post by cjwalther on 2013-05-10
```
dpkg -P linux-generic
```

cured it -- at least for the time being...

---

### Post by fantab on 2013-05-10
Post the output of:
sudo apt-get update

---

