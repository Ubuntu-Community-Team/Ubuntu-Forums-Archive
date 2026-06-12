---
title: "Upgrade to 12.04 fails due to down mirror"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by theophilusdude on 2012-04-27
I get these mirror errors after the upgrade has downloaded many files during the setting sources stage:


W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/main/source/Sources](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/main/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/restricted/source/Sources](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/restricted/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/universe/source/Sources](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/universe/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/multiverse/source/Sources](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/multiverse/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/main/binary-i386/Packages](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/restricted/binary-i386/Packages](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/restricted/binary-i386/Packages)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/universe/binary-i386/Packages](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/universe/binary-i386/Packages)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/multiverse/binary-i386/Packages](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise/multiverse/binary-i386/Packages)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/main/source/Sources](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/main/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/restricted/source/Sources](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/restricted/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/universe/source/Sources](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/universe/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/multiverse/source/Sources](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/multiverse/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/main/binary-i386/Packages](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/main/binary-i386/Packages)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/universe/binary-i386/Packages](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/main/source/Sources](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/main/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/restricted/source/Sources](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/restricted/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/universe/source/Sources](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/universe/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/multiverse/source/Sources](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/multiverse/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/main/binary-i386/Packages](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/main/binary-i386/Packages)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/restricted/binary-i386/Packages](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/universe/binary-i386/Packages](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/universe/binary-i386/Packages)  Unable to fetch file, server said 'Failed to open file.  '
, W:Failed to fetch [ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](ftp://mirror1.cs.washington.edu/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  Unable to fetch file, server said 'Failed to open file.  '
, E:Some index files failed to download. They have been ignored, or old ones used instead.

 There is nothing wrong with my network on this end.  The problem is at your mirror1.cs.washington.edu mirror.

---

### Post by kc1di on 2012-04-27
Not all mirrors sync at the same time so some may not be ready yet.

Give it a few hours and try again.

---

