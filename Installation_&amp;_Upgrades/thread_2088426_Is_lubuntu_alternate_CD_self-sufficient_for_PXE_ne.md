---
title: "Is lubuntu alternate CD self-sufficient for PXE network install a desktop?"
date: 2012-11-26
forum: Installation &amp; Upgrades
---

### Post by Zack Perry on 2012-11-26
Since the regular Ubuntu 12.10 no longer provides the alternate CD, so I downloaded lubuntu alternate-x86_64 CD to test PXE network install.

For the server install, everything went smoothly. But for the desktop, even in my preseed file I specified lubuntu-desktop, the desktop environment didn't get installed.

This is a surprise to me, as with ubuntu-12.04.1-alternate-x86_64.iso, I was able to install the desktop (ubuntu-desktop) successfully. 

Out of curiosity, I did a find . -name "Packages.gz" in the loop mounted lubuntu-alternate-x86_64.iso, and saw the following:

[root@cobbler mnt]# find . -name "Packages.gz"|xargs ls -l
-r--r--r-- 1 root root 382856 Oct 17 00:26 ./dists/quantal/main/binary-amd64/Packages.gz
-r--r--r-- 8 root root     20 Oct 17 00:26 ./dists/quantal/main/binary-i386/Packages.gz
-r--r--r-- 1 root root  30259 Oct 17 00:26 ./dists/quantal/main/debian-installer/binary-amd64/Packages.gz
-r--r--r-- 8 root root     20 Oct 17 00:26 ./dists/quantal/multiverse/binary-amd64/Packages.gz
-r--r--r-- 8 root root     20 Oct 17 00:26 ./dists/quantal/multiverse/binary-i386/Packages.gz
-r--r--r-- 8 root root     20 Oct 17 00:26 ./dists/quantal/restricted/binary-amd64/Packages.gz
-r--r--r-- 8 root root     20 Oct 17 00:26 ./dists/quantal/restricted/binary-i386/Packages.gz
-r--r--r-- 8 root root     20 Oct 17 00:26 ./dists/quantal/restricted/debian-installer/binary-amd64/Packages.gz
-r--r--r-- 1 root root  48538 Oct 17 00:26 ./dists/quantal/universe/binary-amd64/Packages.gz
-r--r--r-- 8 root root     20 Oct 17 00:26 ./dists/quantal/universe/binary-i386/Packages.gz
-r--r--r-- 8 root root     20 Oct 17 00:26 ./dists/quantal/universe/debian-installer/binary-amd64/Packages.gz

So, most Packages.gz files do not have content.  Why?

I would appreciate any tips for getting the desktop install done just with the content of the CD.

Regards,

-- Zack

---

### Post by skmah on 2013-01-30
I would like to know the answer to this as well.

I previously extracted the Ubuntu Alternate CD ISO and did a scripted install via preseed from an http server.

---

