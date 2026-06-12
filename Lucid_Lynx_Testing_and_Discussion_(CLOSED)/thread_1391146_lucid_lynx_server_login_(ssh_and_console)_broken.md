---
title: "lucid lynx server login (ssh and console) broken"
date: 2010-01-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by johnshen on 2010-01-26
I upgraded a box from karmic to lucid alpha with do-release-upgrade, and now i can not log in from ssh or console. looks like no tty was started.

I can get in with recover mode, but any attempt to change password fails with permission denied, password unchanged.

the passwd command is fine. /etc/shadow is readonly (which is normal) by root. nothing unusual.

it is just a test, but I wonder if there is something simple that i missed.

--john

---

### Post by johnshen on 2010-01-26
i figured it out. the pam config files had local modifications that were not compatible with the new version. i reinstalled libpam-runtime and it now works fine.

---

### Post by phillw on 2010-01-26
> **johnshen said:**
> I upgraded a box from karmic to lucid alpha with do-release-upgrade, 


Lucid queries are best posted in the lucid area --> [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)   Pop in, we don't bite :D

Good that you got it working :-)

Regards,

Phill.

---

### Post by adriaan_botha on 2010-04-12
Good Day, Just installed Lynx and couldn't find any ope SSH server, previously this was easy ? How do I configure a ssh server here ?

---

### Post by cariboo on 2010-04-12
Have you got openssh-server installed, as it is not installed by default.

---

