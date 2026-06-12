---
title: "Is /var/cache/apt/archives automatically cleaned?"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by kprateek88 on 2008-03-05
It has often happened to me that I have copied everything in /var/cache/apt/archives from machine A to machine B, and then installed packages on machine B which are already installed on machine A, hoping that there will be no download necessary. I have never deleted the deb files manually or used apt-get clean or autoclean on machine A. However, machine B still wants to download something. Is there some size limit imposed on the /var/cache/apt/archives directory (so that old files are automatically deleted if the limit is exceeded)? If yes, how can I disable it? I won't mind deleting obsolete files, though.

---

