---
title: "Nothing will install"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by jimw on 2008-06-08
Yesterday, I installed 8.04 by the alternate install method.

Because I couldn't get the Thesaurus to work with the Ubuntuized version of OpenOffice, I removed it, but one part of it wouldn't remove, because it was a dependency for other programs.

This meant that I could  not install the "official" OpenOffice either.

So I tried to reinstall the Ubuntu version.  No luck.  In fact, anything I tried to install, KPDF, xpdf, or anything else, I got a message like this:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_2.4.0-3ubuntu6_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_2.4.0-3ubuntu6_i386.deb)
  404 Not Found

I'm sure there's something I'm not doing right, or forgetting to do, but what it could be escapes me.

Anybody got any notions?

JimW

---

### Post by Pumalite on 2008-06-08
System>Administration>Software Sources>Open up all your repos, except src, unless you have a specific need for them. Then:
sudo apt-get update
sudo apt-get dist-upgrade
Now try again.

---

### Post by jimw on 2008-06-09
> **Pumalite said:**
> System>Administration>Software Sources>Open up all your repos, except src, unless you have a specific need for them. Then:
sudo apt-get update
sudo apt-get dist-upgrade
Now try again.

Everything has failed to fetch.  Error message(example):

 Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  404 Not Found

JimW

---

### Post by PmDematagoda on 2008-06-09
Open Software Sources again and change the server location to the Main Server and see if it works now.

---

### Post by jimw on 2008-06-11
> **PmDematagoda said:**
> Open Software Sources again and change the server location to the Main Server and see if it works now.

I was attempting to get the error message for another friend, and found that today, apt-get install works.  

So far I've installed xpdf and KPDF, with no further problem.

Thanks, 

JimW

---

