---
title: "create a cutom kernel that works with linux-restricted-moules"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by melonenmelli on 2007-09-15
hello

i recently found a way to install a custom kernel, that will work perfectly with modules that depend on the official ubuntu kernel version . (e.g. "linux-restricted-modules")

what i did was:

boot another kernel but the recent one.

removed the recent kernel.

compiled the custom kernel (based on the recent ubuntu kernel) with a version- a  revision-number, that matches the latest kernel from the repositories.

that can be achieved by editing the EXTRAVERSION parameter in the MAKEFILE in the sources directory to something like "-11-generic"

then compiled the kernel and made the deb files by

```
sudo make-kpkg --initrd --revision=[actual kernel version, i used "2.6.22-11.32"] binary
```

then installed the debs and i had a custom kernel that fits into my system like the "official" one.

actually i don't see any disadvantages by installing a custom kernel this way especially when you do only minor changes like patching the HDAPS functionality for thinkpad notebooks into it like i did.

has anyone experienced any problems installing a custom kernel this way?

any comments appreciated !

---

