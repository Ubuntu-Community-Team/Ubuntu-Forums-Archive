---
title: "/usr/bin/g++&#12540;3.x  always missing"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by yixuan on 2006-12-21
I am using Ubuntu 6.10 and trying to build an elder project gtk+webcore.

I got the following error.
undefined reference to `__cxa_guard_release`
undefined reference to `__cxa_guard_acquire`

It is said the error occurs because gcc4 version is higher for the project.
So I tried to install gcc3.4 by

$sudo apt-get install gcc-3.4

then
$sudo rm /usr/bin/g++
$sudo ln -s /usr/bin/g++-3.4 /usr/bin/g++

here I make a mistake
$rm /usr/bin/g++-3.4

then I tried to reinstall gcc-3.4
$sudo apt-get remove gcc-3.4
$sudo apt-get install gcc-3.4

but the /usr/bin/g++-3.4 is always missing,
why and how to get it back?
Thanks a lot.

---

