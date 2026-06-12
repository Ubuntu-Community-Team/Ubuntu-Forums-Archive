---
title: "Error downloading packages while updating 10.04 after clean install"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by chivoloco on 2010-08-05
I'm trying to update Ubuntu 10.04 after a clean installation, it downloaded 245 files, and there is an error in the indexes of the 2 last packages:

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_3.2.0-7ubuntu4.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_3.2.0-7ubuntu4.1_all.deb) El tamaño difiere (bad size)
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.2.0-7ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.2.0-7ubuntu4.1_i386.deb) El tamaño difiere (bad size)

This happens even changing the repository to main server or another through "Software origins".  Update-manager doesn't conclude the update because it can't download all the packages.

Please help. Thank you in advance.

---

### Post by lechien73 on 2010-08-05
Since the problem is with OpenOffice, I would be inclined to remove OpenOffice and reinstall it after a successful update. Other people have had to do the same in order to upgrade from 8.04.

---

