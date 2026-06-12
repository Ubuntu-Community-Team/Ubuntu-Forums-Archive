---
title: "set global umask for postfix, mail file has wrong permissions and cannot be read"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by SkyHiRider on 2010-09-17
When postfix creates a mail file it uses the wrong permissions(755) and umask 022. When a new mail is received roundcube cannot read the file due to permissions and hangs. 
How can I set which umask postfix uses?

---

