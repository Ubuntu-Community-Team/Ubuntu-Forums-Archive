---
title: "Upgrading to 7.10 with issues"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by matches on 2007-10-20
Hello,

When I upgrade using update manager. I get an error when it tries to fetch a package to upgrade Aptana. Here is the error:

Failed to fetch [http://ubuntu.mylemontree.com/packages/aptana-beta/Packages.gz](http://ubuntu.mylemontree.com/packages/aptana-beta/Packages.gz) 301 Moved Permanently

If you go to that url the package is there and is downloads fine. Now I am not skilled with Ubuntu /Linuz (yet) so I am not sure what to do with this file. So I wanted to just remove Aptana in hopes that Ubuntu would not try to fetch this file. But I still get the error. Is there a way I can bypass this issue?

Thanks

---

### Post by Pumalite on 2007-10-20
Could you post the exact output from your Terminal? (copy and paste)

---

### Post by matches on 2007-10-20
I'm not using the terminal. I am using the update manager since that is what Ubuntu suggests. Should I be using the terminal.

---

### Post by Pumalite on 2007-10-20
Please.

---

### Post by wgself on 2007-10-20
I am having a similar issue. Here is the message from update manager.
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

---

### Post by Pumalite on 2007-10-20
Comment out (#) the source in your sources.list

---

### Post by wgself on 2007-10-20
Where is the sources.list?
This is the first time I've tried the internet upgrade feature

---

### Post by genterminl on 2007-10-20
wgself - see [http://ubuntuforums.org/showthread.php?t=584050](http://ubuntuforums.org/showthread.php?t=584050).  The name of the medibuntu site changed.  I don't think this is the same problem as matches is having.

---

### Post by wgself on 2007-10-21
That fixed it - thanks

---

