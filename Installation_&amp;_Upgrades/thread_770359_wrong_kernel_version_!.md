---
title: "wrong kernel version ?!?"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by troelskn on 2008-04-27
I have upgraded to hardy and I'm getting really old from trying to get my system stable. Apparently, the newest kernel-version is 2.6.24-16-generic, and my package manager says it's installed. However, the only version available in the bootloader (grub) is 2.6.22-14-generic, which by the way is also what `uname -r` tells me I'm running. Is this expected? Do I have to upgrade, and if so; How?

---

### Post by troelskn on 2008-04-27
While upgrading, I was asked something about "menu.lst". Since I didn't know what it was, and assumed it had to do with the programs menu, I opted to keep existing. Turns out that it's the config file for grub. So I edited the file to allow booting into the newer kernel version. This fixes a lot of problems for me.

---

