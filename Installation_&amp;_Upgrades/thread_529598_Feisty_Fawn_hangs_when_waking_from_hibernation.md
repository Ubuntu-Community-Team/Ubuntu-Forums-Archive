---
title: "Feisty Fawn hangs when waking from hibernation"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by vadania on 2007-08-19
I have installed Ubuntu 7.04 Feisty Fawn and I have the latest updates.
When sleeping, It saves the enviroment just fine.
However, when I try to resume, Ubuntu just hangs up with the logo screen and a few solid lines in the progress bar.

I remember that when I first installed Feisty resume from hibernation was working just fine.
I could try a reinstall, but that would mean losing all my installed applications (I also have applications which are not from the repository - games, antivirus).

---

### Post by pinkertime on 2007-08-21
Hi,
the same happen to me. In order to better understand the problem try to boot without the splash option in grub (/boot/grub/menu.lst). In this way you can see where the process hangs.

For me the process hangs at start when kinit load the swap...:confused:

---

### Post by vadania on 2007-09-03
I reinstalled Ubuntu and now hibernation works out of the box.
Must be something I installed/ or that upgraded to a buggy kernel version (stock 2.6.20-15, updated through System update to 2.6.20-16).

---

