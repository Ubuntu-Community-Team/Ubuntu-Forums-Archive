---
title: "Ubiquity hangs after third-party and install updates dialogue, ubi-partman crash"
date: 2014-07-25
forum: Installation &amp; Upgrades
---

### Post by drakealleg on 2014-07-25
Hey, so I've installed Ubuntu on this laptop before. It's a Toshiba Satellite C55-A5302, it's got Windows 8.1 preinstalled. The disk has an EFI partition, the Windows system partition, two hundred gigs of empty space, and a small recovery partition at the end. When I boot from the 14.04 Live CD and open up ubiquity, the install hangs after the page where it asks if you want third party software and/or to install updates during the installation. To gather some more info, I opened up the terminal, ran 'sudo ubiquity' and tried again. This time, rather than hanging up, it pops up an error message saying ubi-partman crashed with exit code 141. I've got the syslog [here]("https://dl.dropboxusercontent.com/u/11540389/syslog.txt"). I'd appreciate it if somebody more enlightened than I could help figure out what's up and why I can't install Ubuntu.

---

### Post by mikewhatever on 2014-07-26
Looks ok, I don't see any errors.

---

### Post by drakealleg on 2014-07-26
It's not working though, last line of the syslog, ubi-partman 141. Crashses.

---

