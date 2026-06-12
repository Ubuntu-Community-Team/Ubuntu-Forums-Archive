---
title: "subprocess post-removal script returned error exit status 2"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by muskedear on 2008-05-01
There must be a general procedure to cure this issue:


 subprocess post-removal script returned error exit status 2


Any advice as how to proceed systematically?

---

### Post by muskedear on 2008-05-01
Finally, this worked for me:

:/usr/lib$ sudo mv libGL.so.1.2 libGL.so.1.2.old

---

