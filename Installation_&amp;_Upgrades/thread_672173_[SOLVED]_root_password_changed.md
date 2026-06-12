---
title: "[SOLVED] root password changed?"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by freakypcteck on 2008-01-19
Ok i just discovered this problem last night...  i was trying to add a floppy drive to my laptop and discovered that i no longer have su access in terminal...  i upgraded from 7.04 to 7.10 the over day.  i did not manually change the root password,  i rebooted my laptop and tried to login as root, it tells me that the password is incorrect...  and i know it is...  any help world be great. :)

---

### Post by aysiu on 2008-01-19
Ubuntu does not come with a root password enabled, so it's right that you wouldn't have *su* access.

Unless you mean that you had enabled the root account and then root password changed again without you changing it manually a second time.

---

### Post by freakypcteck on 2008-01-19
but before the upgrade i was able to login as root with the password i set for the root account.  unless this is new to the 7.10 that no one has access to root?  but then how would i enable my floppy drive if i do not have access as su? i received an error saying that only the root has access to enable the drive.

---

### Post by aysiu on 2008-01-19
> **freakypcteck said:**
> but before the upgrade i was able to login as root with the password i set for the root account.  unless this is new to the 7.10 that no one has access to root?  but then how would i enable my floppy drive if i do not have access as su? i received an error saying that only the root has access to enable the drive.
Ubuntu uses *sudo* and not *su* for root access. Read more about it here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

