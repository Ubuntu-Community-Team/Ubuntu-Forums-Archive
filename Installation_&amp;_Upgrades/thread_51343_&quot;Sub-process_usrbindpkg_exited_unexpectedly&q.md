---
title: "&quot;Sub-process /usr/bin/dpkg exited unexpectedly&quot;"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by Cerv on 2005-07-23
While running apt-get dist-upgrade to upgrade from warty to hoary I got the message > Unpacking replacement cupsys ...
dpkg: warning - unable to delete old file `/var/spool/cups/certs': Directory not empty
dpkg: ../../lib/dump.c:139: w_booleandefno: Assertion `value==1' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
Anyone know what's happened, and how to fix whatever's gone wrong?

Thanks in advance

---

### Post by Xian on 2005-07-23
EDIT: Just noticed that path in Hoary is /var/lib/cups/certs.

Open nautilus in a terminal with '$ sudo nautilus'
Navigate to /var/spool/cups/
Backup if desired then remove the certs folder.
Repeat the apt procedure.

---

