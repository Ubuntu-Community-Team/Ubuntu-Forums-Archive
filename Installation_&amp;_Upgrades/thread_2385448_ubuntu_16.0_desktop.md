---
title: "ubuntu 16.0 desktop"
date: 2018-02-20
forum: Installation &amp; Upgrades
---

### Post by deheugden on 2018-02-20
Hello,

Is it possibe to install ubuntu-desktop at a ubuntu 16.10 server?
i tried this through sudo apt-get install ubuntu-desktop, but am getting the following output:

reading package lists...done
building dependency tree
reading state information..done
E:\ unable to locate package ubuntu-desktop

hope someone can help.

Thansk in advance.

---

### Post by ubfan1 on 2018-02-20
Ubuntu 16.10 is no longer supported,perhaps that's the problem?  You might try resetting the PPAs to "archive..." something, but better to upgrade to either 16.04 or 17.10.  The server doesn't even have X, so yes,you can install the desktop, but there will be a lot of dependencies to get also.  A better approach would be to simply install the Desktop OS, and maybe add a few server programs.

---

