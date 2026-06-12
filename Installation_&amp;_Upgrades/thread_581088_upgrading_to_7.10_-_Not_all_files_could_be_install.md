---
title: "upgrading to 7.10 - Not all files could be installed"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Bragador on 2007-10-19
Here is what I got from the upgrade manager:

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.bz2) Sub-process bzip2 returned an error code (2)

So, can someone help me or should I download the cd instead? It showed me this error message at step2 in the installation (the channels thing) and it did this to me 3 times out of 3.

:(

---

### Post by abhilash82 on 2007-10-19
> **Bragador said:**
> Here is what I got from the upgrade manager:

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.bz2) Sub-process bzip2 returned an error code (2)

So, can someone help me or should I download the cd instead? It showed me this error message at step2 in the installation (the channels thing) and it did this to me 3 times out of 3.

:(
 Remove these links from the repositories and restart the intall process.

---

### Post by Stemp on 2007-10-19
Your servers are probably extremely busy.
Try to look at [http://buranen.info/?p=185](http://buranen.info/?p=185)

---

### Post by Bragador on 2007-10-24
Well I've waited a few days a used different servers and it did work. Thanks Stemp!

---

