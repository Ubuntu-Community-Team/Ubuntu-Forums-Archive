---
title: "New kernel doesn't show up in boot list after keeping menu.lst"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by temcat on 2010-02-04
Hi all,

I installed Jaunty and all updates. Updates included a new kernel, and when I was asked during the update process what to do with menu.lst, I decided to keep it. As a result, the new kernel doesn't show up in menu.lst. Update-grub doesn't help, deleting menu.lst and recreating it from scratch removes Vista entry from the list. How can I automatically get the full list of kernels and Vista entry without resorting to manual config editing?

There is a corresponding bug: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009)

---

### Post by temcat on 2010-02-04
Solved: I deleted all packages related to the old kernel and then was asked again what to do with menu.lst, to which I responded "Install package maintainer's version". The new kernel an Vista entry now display in grub menu.

---

