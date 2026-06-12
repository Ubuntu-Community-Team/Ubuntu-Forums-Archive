---
title: "Can't upgrade from 7.04 to 7.10"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by ruddy on 2007-12-31
When I try to use the Update Manager to upgrade to 7.10, I keep getting the following errors after the first file fetching and during the next file fetching after it checks the archives:

Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

I would normally do a clean install, but I've got a lot of time and effort invested in configuring my current system. I thought I'd try to do an upgrade to see how that would work out. I've learned not to do that with Windows, but I was hoping that ubuntu would work better. I started to try an install from a 7.10 CD, but I didn't see an upgrade option like in other distributions (e.g., Fedora Core), so I aborted that attempt.

---

### Post by PmDematagoda on 2007-12-31
Go to Software Sources in System>Administration>Software Sources and then untick all the repositories in the Third-Party Software tab, after that is done close the window, you will get a request to reload the sources lists, do that and then you should be able to upgrade Ubuntu.

---

### Post by ruddy on 2008-01-01
That was it! Thanks.

---

