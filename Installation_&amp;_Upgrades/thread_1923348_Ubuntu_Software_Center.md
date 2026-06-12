---
title: "Ubuntu Software Center"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by musabhai6012 on 2012-02-10
The softwares/packages we install through ubuntu s/w center stores a copy of the deb files in /var/cache/apt/archives. Well now my query is, if i take a backup of these files, and later when i install a fresh ubuntu installation, then if i put these backed up files in /var/cache/apt/archives and try to install any of these softwares through s/w center, will ubuntu again download a fresh copy or will it use the backup up copies?

---

### Post by cortman on 2012-02-10
> **musabhai6012 said:**
> The softwares/packages we install through ubuntu s/w center stores a copy of the deb files in /var/cache/apt/archives. Well now my query is, if i take a backup of these files, and later when i install a fresh ubuntu installation, then if i put these backed up files in /var/cache/apt/archives and try to install any of these softwares through s/w center, will ubuntu again download a fresh copy or will it use the backup up copies?

Yes, it will grab from the archive first.

---

