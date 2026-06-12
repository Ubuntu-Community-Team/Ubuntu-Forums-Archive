---
title: "preseed file (adding users)"
date: 2015-05-01
forum: Installation &amp; Upgrades
---

### Post by david.simpson on 2015-05-01
I have added a user via a preseed file. The install still asks (in text mode) if I would like to add any more. Is there anyway to stop this in the preseed file?


( *auto=true priority=critical* are in the pxe default file.)

---

### Post by david.simpson on 2015-07-24
I ended up adding root and another user account (within the preseed)... I think this solved it somewhere along the line

d-i passwd/root-login boolean true
d-i passwd/root-password-crypted password AGENERATEDPW

d-i passwd/make-user boolean true
d-i passwd/user-fullname AUSER
d-i passwd/username string AUSER
d-i passwd/user-default-groups string AGROUP

---

