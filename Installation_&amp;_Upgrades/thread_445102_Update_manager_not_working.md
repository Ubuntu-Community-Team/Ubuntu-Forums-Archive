---
title: "Update manager not working"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by ronbrooks on 2007-05-15
I have tried to update from 6.10 to 7.04 and this is the message I get.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

Dose anyone know why this will not get the up grade for this system.

---

### Post by taurus on 2007-05-15
How exactly were you trying to upgrade from Edgy to Feisty?

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by ronbrooks on 2007-05-15
I used the update manager and I also tried to use the terminal but none of them worked.

---

### Post by Number6 on 2007-05-16
I've had the same problem when using :

gksu "update-manager -c"

that has an extra option for updating the system to the latest release...

I also tried gpg but that didn't seem to help

---

