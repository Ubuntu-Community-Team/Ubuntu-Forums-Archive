---
title: "unable to locate the right apache file"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by mj3 on 2007-03-14
looking for the right apache file that i can do this: 

[B]Search for the line beginning with APACHE_SERVERNAME, which should look like:


APACHE_SERVERNAME=""


Change it to a name that is meaningful to you:


APACHE_SERVERNAME="development"

[/B]

*HINT: it's not in /etc/sysconfig/apache2. can anyone help?

---

