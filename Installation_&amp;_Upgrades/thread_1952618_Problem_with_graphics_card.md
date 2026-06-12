---
title: "Problem with graphics card?"
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by jtreach on 2012-04-04
I've been trying to install xubuntu on a fairly old computer. I reach the initial screen for installation but once I've selected 'install' or 'try before installation' the screen just goes blank save for a flashing underscore. I've now tried lubuntu 11.10 / xubuntu 11.10 / 11.10 alternate / 12.04b2 with no success.

Finding other threads it seems the integrated ATI graphics card might be the source of the problem.

My question is has anybody heard of a solution to this problem and if I can't work with this graphics card do you think buying a new graphics card would solve my problem?

Motherboard : Intel Desktop Board D102GGC2
CPU : Intel Pentium D 3.20 GHZ
GPU : ATI Express 200 series.
Xubuntu Version : 11.10

[http://ubuntuforums.org/showthread.php?t=1758751](http://ubuntuforums.org/showthread.php?t=1758751)
[http://www.thinkdigit.com/forum/open-source/51535-anyone-tried-installing-linux-intel-d102ggc2.html](http://www.thinkdigit.com/forum/open-source/51535-anyone-tried-installing-linux-intel-d102ggc2.html)

---

### Post by QIII on 2012-04-04
That is a "legacy" card no longer supported by AMD/ATI.  The legacy driver is available -- from AMD.  NVIDIA also has a bunch of legacy cards.

Typing from a cell phone right now so giving details would be difficult, but you will probably have to boot with the "nomodeset" option, which should pop up a lot in a search using the search box above.

---

### Post by Mark Phelps on 2012-04-05
The legacy driver that QIII referred to will not work with Ubuntu versions newer than 8.10 due to X-server version incompatibility.

With current Ubuntu versions, you are relegated to using the Radeon open-source drivers -- which are installed by default when you first install Ubuntu.

---

