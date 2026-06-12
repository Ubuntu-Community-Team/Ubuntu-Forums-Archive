---
title: "init.d Zope"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by Licicin on 2007-07-22
How can i automatically restart Zope ?
/var/lib/zope2.9/instance/bin/zopectl restart works fine and i have
zope2.9 in /etc/init.d
what should i do to start Zope with all other programs after reboot?
Thanks.

---

### Post by scxtt on 2007-07-22
what exactly do you mean by "i have zope2.9 in /etc/init.d"?  if you want things to start/stop on boot, you need a script in /etc/rcX.d/ that either starts or kills it ... they're  generally links to /etc/init.d/<program> which can start/stop things based on S or K in the name ...

---

### Post by Licicin on 2007-07-22
Yes,
i have links in rc0.d - rc6.d from init.d

---

### Post by scxtt on 2007-07-23
can you do an **ls -l** in both /etc/init.d and /etc/rc2.d ... ?

---

