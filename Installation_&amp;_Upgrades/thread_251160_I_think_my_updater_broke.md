---
title: "I think my updater broke"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by dgrafix on 2006-09-05
Cant seem to get my latest updates:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/b/bluefish/bluefish_1.0.5-2~dapper1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/b/bluefish/bluefish_1.0.5-2~dapper1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtag1c2a_1.4-4~dapper1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtag1c2a_1.4-4~dapper1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtagc0_1.4-4~dapper1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtagc0_1.4-4~dapper1_i386.deb)
  404 Not Found

---

### Post by Najand on 2006-09-05
> **dgrafix said:**
> Cant seem to get my latest updates:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/b/bluefish/bluefish_1.0.5-2~dapper1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/b/bluefish/bluefish_1.0.5-2~dapper1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtag1c2a_1.4-4~dapper1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtag1c2a_1.4-4~dapper1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtagc0_1.4-4~dapper1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtagc0_1.4-4~dapper1_i386.deb)
  404 Not Found

Use ```
sudo apt-get update
``` to update the package list and then try again. If it fails, maybe there is something wrong with the "au" mirror. Edit your /etc/apt/sources.list and remove "au." from [http://au.archive.ubuntu.com/](http://au.archive.ubuntu.com/).... and then use ```
sudo apt-get update
``` to update the package list and then try again.

---

