---
title: "Postgres - uuid-ossp/adminpack"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by flexpadawan on 2011-10-25
Hi All,

I've successfully installed Ubuntu (11.10) 64bit Server.  Plus, installed postgres from the Ubuntu options menu.

The problem I'm trying to figure out how to install the UUID-OSSP.sql pack.  On any online feed I should only have to run this.

sudo - u  postgres psql < /usr/share/postgresql/9.1/contrib/uuid-ossp.sql

This fails because the contrib folder is not there.  I found it here.
/usr/share/postgresql/9.1/extension/uuid-ossp--1.0.sql

So I tried running it from that location but got errors saying:
ERROR:  could not access file "MODULE_PATHNAME":  no such file or directory.

The same also applies to the admin pack.

Not sure where to go from here.

Thanks in advance to anybody that can help me.

FlexP

---

### Post by flexpadawan on 2011-10-25
Figured out the problem.

Solution:
sudo -u postgres psql   <enter>
create extension "adminpack";
create extension "uuid-ossp";


That's it!

---

