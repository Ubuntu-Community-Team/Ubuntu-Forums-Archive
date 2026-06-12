---
title: "Upgrading the kernel defaults menu.lst to the older kernel"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by DJ_Peng on 2007-10-10
Whenever I did kernel upgrades up to version Ubuntu 7.10, kernel 2.6.22-12-generic when I did the required reboot my Grub menu defaulted to the newest kernel, but last week when I took the upgrade to Ubuntu 7.10, kernel 2.6.22-13-generic the default selection was the previous kernel, not the new one. I know there were some issues with that kernel, so when I took the new update several minutes ago I figured the Grub menu would default to the new version that I had just installed, Ubuntu 7.10, kernel 2.6.22-14-generic. But when I came out of the reboot and got the Grub menu it defaulted to the -13 kernel. I know it's an easy fix (changing the default in menu.lst from 2 to 0), but why am I suddenly having to do this with two upgrades in a row?

---

