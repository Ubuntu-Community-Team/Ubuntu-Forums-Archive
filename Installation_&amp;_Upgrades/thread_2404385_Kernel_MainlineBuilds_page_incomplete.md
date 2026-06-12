---
title: "Kernel MainlineBuilds page incomplete?"
date: 2018-10-23
forum: Installation &amp; Upgrades
---

### Post by corradoventu on 2018-10-23
page [https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds) does not say that linux-modules should also be downloaded but I don't know how to report the problem.

the page just say:
```
Choose the proper upstream kernel files

From the below example, if one is using a 64-bit/amd64 architecture you would want those files marked A.
If you are using a 32-bit/i386 architecture, B.

A  linux-headers-3.14.4-031404-generic_3.14.4-031404.201405130853_amd64.deb
B  linux-headers-3.14.4-031404-generic_3.14.4-031404.201405130853_i386.deb
AB linux-headers-3.14.4-031404_3.14.4-031404.201405130853_all.deb
A  linux-image-3.14.4-031404-generic_3.14.4-031404.201405130853_amd64.deb
B  linux-image-3.14.4-031404-generic_3.14.4-031404.201405130853_i386.deb

```
But I was unable to complete the install without linux-modules.

---

### Post by Doug S on 2018-10-24
I edited the wiki page in an attempt to reflect the current version of the mainline build directory. See if it addresses your concerns: [https://wiki.ubuntu.com/Kernel/MainlineBuilds]("https://wiki.ubuntu.com/Kernel/MainlineBuilds").

By the way, the libssl example under the [package versions issues]("https://wiki.ubuntu.com/Kernel/MainlineBuilds#Version_of_package_needed_by_installer_is_too_old") section, has been driving me crazy for many months now. Why? because the mainline kernel doesn't actually depend on it. If I compile my own kernel it works fine. (My main test computer is still on 16.04.)

---

### Post by corradoventu on 2018-10-25
Yes thanks, this solves my concerns
thanks again

---

