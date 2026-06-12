---
title: "No entry in ../init.d"
date: 2015-04-08
forum: Installation &amp; Upgrades
---

### Post by cle-ziskind on 2015-04-08
While troubleshooting apt-get problems, I noticed that Dovecot (running on the system) has no entries in /etc/rc?.d /etc/init.d. Isn't that a problem, that it won't start on boot? How can I fix it, please?

Thanks!

---

### Post by cle-ziskind on 2015-04-08
This wasn't it:

# update-rc.d dovecot defaults
update-rc.d: /etc/init.d/dovecot: file does not exist

---

### Post by cle-ziskind on 2015-04-13
What does everyone think about 
a) saving dovecot.conf; 
b) apt-get remove dovecot*; 
apt-get install dovecot; 
d) put back the .conf file?

---

### Post by ian-weisser on 2015-04-13
Looks like Dovecot was converted from sysvinit to Upstart.
Look in /etc/init/dovecot.conf

---

