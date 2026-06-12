---
title: "Upgrade buttton not available for 9.10"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by The_Weaver on 2009-12-15
Went to upgrade my Netbook from 9.04 to 9.10 and found the upgrade button was missing. It was there for a while when 9.10 initially came out, but at some point disappeared.
Any thoughts ?

---

### Post by bluelamp999 on 2009-12-15
Just a thought but try *System>Administration>Software Sources* and on the Update tab make sure the 'Show new distribution releases:' is set to 'Normal releases'

However, the general consensus seems to be that a clean install is by far the best option for 9.10

---

### Post by The_Weaver on 2009-12-15
Thanks, I was hoping to save the pain of a clean install.

---

### Post by The_Weaver on 2009-12-15
Sorted it had to run :

gksudo update-manager -d

---

### Post by bluelamp999 on 2009-12-15
Cool! Good luck with the upgrade!

---

