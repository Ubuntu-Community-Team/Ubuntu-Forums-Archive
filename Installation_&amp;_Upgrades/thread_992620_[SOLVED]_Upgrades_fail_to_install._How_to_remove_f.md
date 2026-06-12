---
title: "[SOLVED] Upgrades fail to install. How to remove from command line?"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by malangaman on 2008-11-24
The latest package of 15 upgrades for OpenOffice and Pidgin failed to install due to " missing newline.". They can't be removed with synaptic since it produces the same error. How can this last, uninstallable failed 236 meg upgrade be removed from Hardy 8.04 using the command line?
Is there an Ubuntu "system restore" equivalent?

---

### Post by malangaman on 2008-11-25
This turned out to be bug #108189 in dpkg(Ubuntu):

[I]APt-get, adept, and the restricted drivers manager might halt installing packages when one or more of the files in:
/var/lib/dpkg/info/
is corrupt.
The error shown will be either:
files list file for package `*' is missing final newline
Or:
files list file for package `*' contains an empty filename

Where * start is a random but steady "per install" package name.[/I]

described here:
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189)
I followed the solution here:
[http://ubuntuforums.org/showthread.php?t=12737&page=2](http://ubuntuforums.org/showthread.php?t=12737&page=2)

and after a fun 2 hours of carefully following directions, the problem is solved and we are back in business!

---

