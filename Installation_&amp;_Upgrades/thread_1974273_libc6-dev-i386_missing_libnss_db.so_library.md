---
title: "libc6-dev-i386 missing libnss_db.so library"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by masuch on 2012-05-05
Hi,

I installed package libc6-dev-i386 on precise.
but I cannot find libnss_db.so library.

apt-file search libnss_db:
libc6-dev-i386: /usr/lib32/libnss_db.so

but /usr/lib32/libnss_db.so is link to /lib32/libnss_db.so.2

but /lib32/libnss_db.so.2 does not exist.
and no library to point to does not exist either.

reinstall did not helped.

Where is this 32 bit library comes from ?
Where can I get it ?
package libc6-dev-i386_2.15-0ubuntu10_amd64.deb does not contain it.


thank you for help,
kind regards,
M.

---

